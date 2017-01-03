Symfony Edit In Place
=====================

The Symfony Edit In Place feature allow to edit translations directly in the context of the page, without altering the display styles and presentation.

Users are able to change any translated text directly on a web page, and save them to your configured translation configurations.

.. figure:: /assets/image/edit-in-place-demo.gif
    :width: 900px
    :align: center
    :alt: Demonstration of the Edit In Place feature

*Some translated string can't be translated via this feature, like HTML Input placeholder or title tag for example. The JavaScript part is using ContentTools by Anthony Blackshaw, which use the HTML contenteditable attribute.*

Configuration
-------------

.. code-block:: yaml

    # config/config.yml
    translation:
      # ..
      edit_in_place:
        enabled: true
        config_name: default # The configuration to use
        activator: php_translation.edit_in_place.activator # The activator service id
      # ..

.. code-block:: yaml

    # config/routing.yml
    _translation_edit_in_place:
      resource: '@TranslationBundle/Resources/config/routing_edit_in_place.yml'
      prefix:  /admin

.. note::

    When you include the ``routing_edit_in_place.yml`` to expose the controller
    that saves the modifications you should be aware of the following:

    - The routes **must** be in a protected area of your application
    - The routes **must** be in the production routing file if you want allow real users to use the feature.


.. note::

    Make sure the Bundle assets are installed via ``bin/console assets:install``

Usage
-----

To see the editor options on a page, the ``php_translation.edit_in_place.activator`` service needs to allow the Request. By default we provide a simple Activator based on a flag stored in the Symfony Session.

You can activate the editor by calling:

.. code-block:: php

    $container->get('php_translation.edit_in_place.activator')->activate();

Then browse your website and you should see the blue Edit button on the top left corner. If you change a translation and hit the Save button, the modifications are saved for the current locale. So if you want to edit a German translation you have to go on the German version of your website.

You can deactivate the editor by calling:

.. code-block:: php

    $container->get('php_translation.edit_in_place.activator')->deactivate();

Those calls have to be implemented by yourself.

Building your own Activator
---------------------------

You can change the way the editor is activated by building your own Activator service, all you have to do in implement the ``Translation\Bundle\EditInPlace\ActivatorInterface`` interface.

For example if you wish to display the editor based on a specific authorization role you could implement it that way:

.. code-block:: php

    <?php

    namespace AppBundle;

    use Symfony\Component\HttpFoundation\Request;
    use Symfony\Component\Security\Core\Authorization\AuthorizationCheckerInterface;
    use Symfony\Component\Security\Core\Exception\AuthenticationCredentialsNotFoundException;
    use Translation\Bundle\EditInPlace\ActivatorInterface;

    class RoleActivator implements ActivatorInterface
    {
        /**
         * @var AuthorizationCheckerInterface
         */
        private $authorizationChecker;

        public function __construct(AuthorizationCheckerInterface $authorizationChecker)
        {
            $this->authorizationChecker = $authorizationChecker;
        }

        /**
         * {@inheritdoc}
         */
        public function checkRequest(Request $request = null)
        {
            try {
                return $this->authorizationChecker->isGranted(['ROLE_ADMIN']);
            } catch (AuthenticationCredentialsNotFoundException $e) {
                return false;
            }
        }
    }


.. code-block:: yaml

    # services.yml
    services:
      my_activator:
        class: AppBundle\RoleActivator
        arguments: ["@security.authorization_checker"]

And then use this new activator in the bundle configuration:

.. code-block:: yaml

    # config/config.yml
    translation:
      # ..
      edit_in_place:
        activator: my_activator
      # ..

The Editor toolbox for HTML
---------------------------

What is allowed inside the edited text is handled by our JavaScript. So if you follow the :doc:`../best-practice/index` and finish your translation keys with ``.html`` when you want to allow HTML, the editor comes with full power:

.. figure:: /assets/image/demo-html-editor.png
    :width: 992px
    :align: center
    :alt: HTML Editor options

Please refer to ContentTools_ documentation for more information.

.. _ContentTools: http://getcontenttools.com/


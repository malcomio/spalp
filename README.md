# Single Page App Landing Page module for Drupal

This module provides a standardised way for site managers to configure and serve
single-page applications as pages in a Drupal site.

This approach has been described as “Progressively Decoupled”
- see https://dri.es/how-to-decouple-drupal-in-2018

## App Landing Page content type
The module defines a content type to provide a landing page for each app.

All relevant configuration and text used in the app is stored on this node,
and made available as a JSON endpoint to be consumed by the app.

## JSON endpoints
TODO: info on URLs, translations, revisioning

## Extending the module
See the spalp_example module for a simple implementation.

Create a module that implements EventSubscriber to react on "SpalpAppIdsAlterEvent::APP_IDS_ALTER" event. EventSubscriber will provide module's app id to list of available app ids.

The app ID provided by your module will be used as the ID of
a <div> element on the node view.
This can be used as your main app element.

### Default configuration and application text
Create a JSON file in your module directory called  mymodule.config.json.
See spalp_example.config.json for an example of the structure.

When your module is installed, an unpublished `applanding` node will be created,
with the module name selected as the `field_spalp_app_id` value.

`appConfig` values will be stored on the node's `field_spalp_app_config` field.
`appText` will be stored on the node's `field_spalp_app_text` field.

### Adding your app's assets
Define a library for your assets as per https://www.drupal.org/node/2274843.
If the library name matches your module's machine name, the spalp module
will take care of attaching the library when the app landing node is viewed.

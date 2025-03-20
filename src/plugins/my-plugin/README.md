# my-plugin

How to add a new content type to a plugin:

**Prerequisites:**

- A plugin must be enabled in the `config/plugins.ts` file.
- The plugin must be installed and available in the `./src/plugins` directory.

Once you have a plugin enabled, inside the plugin folder, you can add a new content type to it by following these steps:

1. Inside `./server/src/content-types` directory create a new folder named after your content type. In my case, I'm going to create a folder named `content`.

2. Inside this folder, create a file named `schema.json`. This file will contain the schema of your content type.

Here is an example of a schema.json file:

``` json
{
  "kind": "collectionType",
  "collectionName": "content",
  "info": {
    "singularName": "content",
    "pluralName": "contents",
    "displayName": "Content"
  },
  "options": {
    "draftAndPublish": false
  },
  "pluginOptions": {
    "content-manager": {
      "visible": true
    },
    "content-type-builder": {
      "visible": true
    }
  },

  "attributes": {
    "title": {
      "type": "string"
    }
  }
}
```

3. Inside the same folder, create a file named `index.ts`. This file will export the content type.

``` ts
import schema from './schema.json';

export default {
  schema,
};
```

4. Finally in the `content-types` folder update or create `index.ts` file and export the content type.

``` ts
import content from "./content";

export default {
  content,
}
```

Finally, in the plugin folder, update the `./src/plugins/my-plugin` run the following command to build your plugin.

``` bash
npm run build
```

And in the root folder, run the following command to restart your Strapi server.

``` bash
npm run develop
```

You should now be able to see your new content type in the Strapi admin panel.





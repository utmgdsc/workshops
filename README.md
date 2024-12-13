# GDSC UTM Workshop Archive

Workshop slides are now available in the repository, ad-free, adaptable, and for your enjoyment! We hope you enjoy the slides and learn something new from them. If you have any questions, feel free to contact us on our Discord server!

A friendlier way to view these files may be accessed through [our workshop archive page](https://www.gdscutm.com/past-workshops) on our website.

<p xmlns:cc="http://creativecommons.org/ns#" >This work is licensed under <a href="http://creativecommons.org/licenses/by-nc-sa/4.0/?ref=chooser-v1" target="_blank" rel="license noopener noreferrer" style="display:inline-block;">Attribution-NonCommercial-ShareAlike 4.0 International<img style="height:22px!important;margin-left:3px;vertical-align:text-bottom;" src="https://mirrors.creativecommons.org/presskit/icons/cc.svg?ref=chooser-v1"><img style="height:22px!important;margin-left:3px;vertical-align:text-bottom;" src="https://mirrors.creativecommons.org/presskit/icons/by.svg?ref=chooser-v1"><img style="height:22px!important;margin-left:3px;vertical-align:text-bottom;" src="https://mirrors.creativecommons.org/presskit/icons/nc.svg?ref=chooser-v1"><img style="height:22px!important;margin-left:3px;vertical-align:text-bottom;" src="https://mirrors.creativecommons.org/presskit/icons/sa.svg?ref=chooser-v1"></a></p>

## Contributing a new workshop
1. [Fork this repository](https://github.com/utmgdsc/workshops/fork).
2. Edit the `metadata.yml` file, located in the folder of the year you want to add a workshop to.
3. Locate or create a new category for the workshop, which are the keys in the `metadata.yml` file.
4. Refer to the schema below to fill in the details of the workshop. Workshops are represented as objects in the array of the category.
   - Slides can be uploaded to the same directory as the `metadata.yml` file, and referenced by the filename in the `slides` property.
5. [Create a pull request](https://github.com/utmgdsc/workshops/compare) to merge your changes into the main repository.

## Schema

Each file in /:year/metadata.yml has the following schema:

- Each key represents a category of workshop.
- Each key contains an array of objects, where each object represents a single workshop.
- The object has the following properties:

| Property    | Type   | Optional | Description                                                                                   |
| ----------- | ------ | -------- | --------------------------------------------------------------------------------------------- |
| name        | string | No       | The name of the workshop.                                                                      |
| host        | string[] | No       | An array of the names of the hosts of the workshop.                                           |
| description | string | No       | The title of the workshop.                                                                     |
| date        | string | No       | The date of the workshop in MM-DD format, since the year is already specified in the file path. |
| code        | string | Yes      | The URL to the starter code code of the workshop.                                              |
| slides      | string | Yes      | The filename of the slides of the workshop. The slides must be in the same directory as the metadata.yml file. |
| recording   | string | Yes      | The URL to the recording of the workshop.                                                      |

You may view the [JSON schema](./schema.json) for detailed information.

## Static API

The "API" allows programmatic access to the workshop archive. It is not a true API, but rather a collection of YML files that can be accessed through GET requests.

### GET /pages.yml

Returns a list of more links to every year's workshop archive.

#### Example Response

```yml
- /2021/metadata.yml
- /2022/metadata.yml
- /2023/metadata.yml
```

### GET /:year/metadata.yml

Returns a list of all workshops in the specified year.

#### Example Response

```yml
Category Name 1:
- name: Example Workshop
  date: '11-06' # MM-DD
  host:
  - Host
  description: This is an example workshop.
  code: https://github.com/utmgdsc/starter-code          # optional
  slides: A pdf file in the same directory as this file. # optional
  recording: https://www.youtube.com/watch?v=dQw4w9WgXcQ # optional

Category Name 2:
- name: Example Workshop
  date: '11-06'
  host:
  - Host
  description: This is an example workshop.
```

### GET /all.yml

Returns a list of all workshops in the archive.

#### Example Response

```yml
2023:
  Category Name 1:
  - name: Example Workshop
    date: '11-06'
    host:
    - Host
    description: This is an example workshop.
    code:
```

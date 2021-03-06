#### JonlilCKFinderBundle

For documentation on CKFinder http://cksource.com/ckfinder    
If you planing to configure ckeditor a little bit more :) https://github.com/egeloen/IvoryCKEditorBundle

1) Installation
-------------------------

```json
"require": {
    "jonlil/ckfinder-bundle": "dev-master"
}
```

```php
public function registerBundles()
{
    $bundles = array(
        new Ivory\CKEditorBundle\IvoryCKEditorBundle(),
        new Jonlil\CKFinderBundle\JonlilCKFinderBundle('IvoryCKEditorBundle'),
    );
}
```

2) Configuration
--------------------------

##### Routing
```yaml
# app/config/routing.yml

ck_finder:
    resource: "@JonlilCKFinderBundle/Resources/config/routing/routing.yml"
    prefix: /ckfinder
```

##### For usage with amazon s3
```yaml
# app/config/config.yml

jonlil_ck_finder:
    license:
        key: ""
        name: ""
    baseDir: "/"
    baseUrl: "http://s3.amazonaws.com"
    service: "s3"
    accessKey: ""
    secret: ""
    bucket: ""
```
##### For usage with native php storage
```yaml
jonlil_ck_finder:
    license: # optional, can be used in demo mode also
        key: ""
        name: ""
    baseDir: "%assetic.read_from%"
    baseUrl: "/userfiles/"  # path where your files will be stored
    service: "php"
```

3) Usage
--------------------------
```php

# in your symfony2 form - add this
public function buildForm (FormBuilderInterface $builder, array $options)
{
    $builder
        ->add('title')
        ->add('text', 'ckfinder')
        ->add('createdAt')
        ->add('updatedAt')
    ;
}
```

4) Todos
---------------------------
Fix amazon s3 thumbnails - Refer to this project https://github.com/jonlil/ckfinder



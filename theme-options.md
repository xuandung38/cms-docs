# Theme options

- [Basic usage](#basic-usage)

<a name="basic-usage"></a>
## Basic usage of theme options

Below is basic usage of theme options.

```php
theme_option()
    ->setSection([ // Set section with no field
        'title' => __('General'),
        'desc' => __('General settings'),
        'id' => 'opt-text-subsection-general',
        'subsection' => true,
        'icon' => 'fa fa-home',
    ])
    ->setSection([ // Set section with some fields
        'title' => __('Logo'),
        'desc' => __('Change logo'),
        'id' => 'opt-text-subsection-logo',
        'subsection' => true,
        'icon' => 'fa fa-image',
        'fields' => [
            [
                'id' => 'logo',
                'type' => 'mediaImage',
                'label' => __('Logo'),
                'attributes' => [
                    'name' => 'logo',
                    'value' => null,
                ],
            ],
        ],
    ])
    ->setField([ // Set field for section
        'id' => 'copyright',
        'section_id' => 'opt-text-subsection-general',
        'type' => 'text',
        'label' => __('Copyright'),
        'attributes' => [
            'name' => 'copyright',
            'value' => '© 2016 Botble Technologies. All right reserved.',
            'options' => [
                'class' => 'form-control',
                'placeholder' => __('Change copyright'),
                'data-counter' => 120,
            ]
        ],
        'helper' => __('Copyright on footer of site'),
    ])
    ->setArgs(['debug' => true]);
```

## Supported fields

- Input (text, password, email, number)

```
->setField([
        'id' => 'field_name',
        'section_id' => 'opt-text-subsection-section-id',
        'type' => 'text', // text, password, email, number
        'label' => __('Field label'),
        'attributes' => [
            'name' => 'field_name',
            'value' => null, // default value
            'options' => [
                'class' => 'form-control',
                'placeholder' => __('Placeholder (optional)'),
                'data-counter' => 120,
            ]
        ],
        'helper' => __('Helper text (optional)'),
    ])
```

- Select

```
->setField([
    'id' => 'field_name',
    'section_id' => 'opt-text-subsection-section-id',
    'type' => 'select', // select or customSelect
    'label' => __('Field label'),
    'attributes' => [
        'name' => 'field_name',
        'data' => [ // Array options for select
            0 => 'No',
            1 => 'Yes',
        ],
        'value' => null, // default value
        'options' => [
            'class' => 'form-control',
        ],
    ],
])
```

- Image

```
->setField([
    'id' => 'banner-ads',
    'section_id' => 'opt-text-subsection-section-id',
    'type' => 'mediaImage',
    'label' => __('Image'),
    'attributes' => [
        'name' => 'banner-ads',
        'value' => null,
    ],
])
```

- Editor (Ckeditor or TinyMCE, you can change it in settings)

```
->setField([
    'id' => 'field_name',
    'section_id' => 'opt-text-subsection-section-id',
    'type' => 'editor',
    'label' => __('Field label'),
    'attributes' => [
        'name' => 'field_name',
        'value' => null, // Default value
        'options' => [ // Optional
            'class' => 'form-control theme-option-textarea',
            'row' => '10',
        ],
    ],
    'helper' => __('Helper for this field (optional)'),
])
```

- On/Off (Radio button)

```
->setField([
    'id' => 'field_name',
    'section_id' => 'opt-text-subsection-section-id',
    'type' => 'onOff',
    label' => __('Field label'),
    'attributes' => [
        'name' => 'field_name',
        'value' => 1,
        'data' => [
            0 => 'No',
            1 => 'Yes',
        ],
        'options' => [],// Optional
    ],
    'helper' => __('Helper for this field (optional)'),
]);
```

- Custom Radio

```
->setField([
    'id' => 'field_name',
    'section_id' => 'opt-text-subsection-section-id',
    'type' => 'onOff',
    label' => __('Field label'),
    'attributes' => [
        'name' => 'field_name',
        'values' => [
            [0, 'No'],
            [1, 'Yes'],
        ],
        'selected' => 1,
        'options' => [],// Optional
    ],
    'helper' => __('Helper for this field (optional)'),
]);
```

- Custom Select

``` 
->setField([
    'id' => 'field_name',
    'section_id' => 'opt-text-subsection-section-id',
    'type' => 'onOff',
    label' => __('Field label'),
    'attributes' => [
        'values' => [
            ['field_name[]', 1, 'Option 1'],
            ['field_name[]', 2, 'Option 2'],
        ],
        'name' => 'whatever', // It will be removed soon
    ],
    'helper' => __('Helper for this field (optional)'),
]);
```
# yii2-dynamicvalue

### 1. Download
Yii2-DynamicValue extension can be installed using composer. Run the command bellow in console to download 
and install Yii2-swap:

```bash
composer require kirillantv/yii2-dynamicvalue
```

or you can add following require to composer.json:
```bash
...
"require": {
  ...
  "kirillantv/yii2-dynamicvalue": "*"
  ...
}
```
### 2. Usage
The DynamicValue widgets is used to display dynamic content depending on value of input data. 
You can use this widget adding following code to your view file and config `items`:
```php
<?= DynamicValue::widget([
  'data' => $model,
  'column' => 'status',
  'items' => [
      [
          'value' => 1,
          'label' => 'Disable order',
          'link' => ['order/disable', 'id' => $model->id],
          'options' => ['class' => 'btn btn-danger btn-block']
  ],
      [
          'value' => 0,
          'tag' => 'span',
          'label' => 'Is done',
          'options' => ['class' => 'btn btn-success btn-block']
  ]]
  ]);
```
Widget has following parametres:

`data` is model with your data. It would be nice if it will be active record model.

`column` is property of your model or column of DB.

`items` is array of configuration arrays depending on values of the column. You can configure it
by the next way:

`value` is value of column according to the current configuration. If you don't specify it, widget will take 
array indexes as value. Therefore you can set `items` array without `value` as follow:
```php
'items' => [
    1 => [
        ...
    ],
    3 => [
        ...
    ],
    'textValue' => [
        ...
    ]
]
```

`label` is a text output.

`link` is optional parameter. If you will set it, widget will render a hypertext link.

`encode` - boolean property. If you want to encode label you have to set it true. By default label is not encoded.

`tag` is HTML tag wrapping your label. Ignored if you set `link`. By the default, it renders `<div>`

`options`is array the tag options in terms of name-value pairs.

**Note! By default, widget provides content for 'status' column, such as, active = 1, archive = 0 and error = -1 status.
So if any of these values is not specified in config array the default content will be render. **

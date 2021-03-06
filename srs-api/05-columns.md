﻿# SRS/columns

Optional XML element with column additional formatting

## Example

``` xml
<SRS>
<!-- ... removed for clarity -->
<columns>
	<column name="product" type="tlink" width="300" mobile="true" url="/mportal/417-portal-product/tasks?id={productID}"/>
	<column name="imsprofil_social" hidden="false" label="Instagram" type="turl_blank" url="https://www.instagram.com/{imsprofil_social}" />
</columns>
</SRS>
```

## Attributes

> Important notice ampersand (&) must be replace with &amp; in attributes

- `desktop` [true], show/hide column
- `mobile` [true] , visible in mobile
- `title`, optional title for name
- `url`, optional URL http://pandaa.io/item/{anycolumnname}/{anycolumnname} 
- `label`, optional
- `name`, required
- `required`, optional true/false 
- `type` , additional formatting
- `permission`, optional column level permission
- 🆕 `css`  - custom style for element, Example `background-color:red`

## Column `type`

### Default

List of autodiscover types from database schema

- `tguid` 
- `tdate` (Date)
- `tbool`  (Bool)
- `tinteger`  example 2 (Number)
- `tdecimal` , example 2.02  (Decimal)
- `tstring`

### Custom

List of custom types from database schema

- `tcolor_progress`
- `tinput_number`
- `tinput_text`
- `tinput_bool`
- `tlink` -  internal link
- `tlink_icon`  - internal link with icon font awesome 4 icon
  - column.url - url 
  - column.css - font awesome 4 class  https://fontawesome.com/v4.7.0/icons/ example `fa fa-bar-chart`
- `tlink_download`
- `tcomputed` , example : {column1} * {column2} /2 ,  getComputed(column.url,row,table.columns)
- `turl_blank` - external linking
- `turl_download` 
- `turl_post`
- `turl_tag`
- `turl_progress`
- `tformat_bytes` , old: fileSize,  (Human readable size input bytes)
- `ttag` 
- `tmarkdown`, renders markdown server side
- `tstring_multi` -- multiline Text with Line breaks similar to HTML `pre` tag
- `timg` - image token from repository `example: ea4cc594-fd85-ea11-80e1-9c8e994dc647.jpg`
- **[obsolete use timg]** `timgcircle` - rounded image from repository `example: ea4cc594-fd85-ea11-80e1-9c8e994dc647.jpg`
- 🆕 `timg` - see timg examples section


####  Examples:  `timg` 

get file from files 
```xml
<column name="logo" type="timg" url="/api/files/26EFEED6-CDEF-E911-80DA-9C8E994DC647.png?w=150" />
```

examples get img logo 
```xml
<column name="logo" type="timg" url="/client/images/logo.png?w=150" />
```

examples get qrcode
```xml
<column name="qr" type="timg" label="Order code" css="width:100px" url="/api/system/qrcode?code={qr}" />
```

examples get BAR code
Supported type =  Code128 , ean13, Code93
```xml
<column name="qr" type="timg" label="Order code" css="width:100px" url="/api/system/barcode?code={qr}&type=code128" />
```

  
### Examples:  `turl_blank`  - external linking

```xml
<!--Redirect to external page-->
<column name="COMMISIONNAME" title="test" label="test"  type="turl_blank" url="http://test.com/test?commisionID={commisionID}" />
```

### Examples:  `tstring_multi`  - external linking

SQL Server Example:

``` sql
SELECT 'Hello' + CHAR(13) + CHAR(10) + 'World'
```

### Examples `tstring_multi`

Text with Line breaks similar to HTML `pre` tag

SQL Server Example:

``` sql
SELECT 'Hello' + CHAR(13) + CHAR(10) + 'World'
```


## Appendix , special column names

###  if column.name = ROWCOLOR 

you can define hexadecimal color for row. Example colors https://htmlcolorcodes.com/color-chart/material-design-color-chart/




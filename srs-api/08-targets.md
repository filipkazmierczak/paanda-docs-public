# SRS/targets

Target section is optional.

## Attributes

- `type` 
- `renderer` (optional template name)
- `label` - optional label
- `title` - optional title

## Target `type`



- Basic types
  - `get` (default with cache respect) Returns JSON
  - `post` (always new data ) Returns JSON
  - `object` Returns JSON as object "DaTA NODE"
  - `xlsx` Excel  returns application/octet-stream
  - `html` Tables printout friendly, only columns with  export=true by default or desktop=true 
  - `html-all-coll` All columns
  - `txt` Raw text 
  - `svg` REturns Image for first row of table name matching renderer name, 
    - `row[0][0]` - required, value
    - `row[0][1]` - optional, title
    - `row[0][2]` - optional, background color
    - `row[0][3]` - optional, foreground color
- Preprocessed
  - `md` markdown renderer of `app\[renderer].html` template
  - `pdf` Renders pdf file ,returns application/pdf, renderer of `app\[renderer].html` template
  - `pdfmd` Renders pdf file ,returns application/pdf, renderer of `app\[renderer].html` template
  - `htmltemplate`   Renders html file, renderer of `app\[renderer].html` template


## Example

~~~ xml
<SRS>
  <!-- .... removed for clarity-->
  <targets>
        <target  type="pdf" label="PDF" renderer="order-confirmation-print"></target>
        <target  type="pdfmd" label="PDF" renderer="order-confirmation-print"></target>
        <target  type="xlsx" label="xlsx"></target>
        <target  type="html" label="html" renderer="order-confirmation-print"></target>
        <target  type="htmlmd" label="html" renderer="order-confirmation-print"></target>
        <target  type="txt" label="txt" renderer="order-confirmation-print"></target>
        <target  type="post"></target>
        <target  type="get"></target>
  </targets>
</SRS>
~~~


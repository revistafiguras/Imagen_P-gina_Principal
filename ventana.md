## Código para colocar ventana en la página Principal de OJS 3

Vamos a la ruta en el servidor: `/var/www/html/ojs/templates/frontend/pages` y entramos al archivo `indexJournal.tpl`.

Una vez dentro del archivo `indexJournal.tpl` buscamos esta parte del código al final del archivo:

```smarty
{* Latest issue *}
{if $issue}
  <section class="current_issue">
    <a id="homepageIssue"></a>
    <h2>
      {translate key="journal.currentIssue"}
    </h2>
    {include file="frontend/objects/issue_toc.tpl" heading="h3"}
    <a href="{url router=$smarty.const.ROUTE_PAGE page="issue" op="archive"}" class="read_more">
      {translate key="journal.viewAllIssues"}
    </a>
  </section>
{/if}
```

        

Se agrega la siguiente etiqueta div con la class fixed-bh después del cierre de la etiqueta if

```html
<div class="fixed-bh"><img src="https://revistafiguras.acatlan.unam.mx/public/journals/1/Ventana-Sonido-ciudad.png">
</div>
```


quedaría así...opcional etiqueta smarty {*Bauhaus*} esta etiqueta es un comentario para la ubicación del código.

```smarty
 {* Latest issue *}
        {if $issue}
                <section class="current_issue">
                        <a id="homepageIssue"></a>
                        <h2>
                                {translate key="journal.currentIssue"}
                        </h2>
                        {include file="frontend/objects/issue_toc.tpl" heading="h3"}
                        <a href="{url router=$smarty.const.ROUTE_PAGE page="issue" op="archive"}" class="read_more">
                                {translate key="journal.viewAllIssues"}
                        </a>
                </section>
        {/if}
        {* Bauhaus *}
        <div class="fixed-bh"><img src="https://revistafiguras.acatlan.unam.mx/public/journals/1/Ventana-Sonido-ciudad.png" alt="texto alternativo"></div>        
{include file="frontend/components/footer.tpl"}
```
Si se quiere modificar el tamaño a lo ancho, tendrá que modificarse desde la clase fixed-bh (class)


## Ruta del archivo CSS y propiedades de la clase
Ingresar a la ruta: /var/www/html/ojs/public/journals/1 y agregar al archivo styleSheet.css el nombre del fondo de la ventana en su respectiva 
clase como el ejemplo siguiente: 
  ```css
    .fixed-bh {
        display: flex;
        flex-wrap: wrap;
        background-image: url(https://revistafiguras.acatlan.unam.mx/public/journals/1/Fondo-Sonido-ciudad.jpg);
        background-repeat: no-repeat;
        background-attachment: fixed;
        background-size: 69% 100%; 
        }
  ```


La imagen y el fondo de la ventana que vayan a agregarse debe de estar en la ruta: /var/www/html/ojs/public/journals/1
Esta imagen debe enviarse desde una computadora al servidor con el comando scp. 

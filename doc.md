# Documentación del Proceso de Creación del Diseño Responsive usando Flexbox

En este proyecto, se ha creado un diseño web responsive utilizando Flexbox. A continuación, se detalla el proceso de desarrollo y los conceptos clave utilizados.

## Estructura HTML

Se creó un archivo `index.html` que sigue la estructura básica de una página web. Los componentes solicitados se incluyeron de la siguiente manera:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Responsive Layout</title>
    <link rel="stylesheet" href="index.css" />
  </head>
  <body>
    <header class="header">
      <div class="logo">
        <a href="/">My Logo</a>
      </div>
      <nav class="menu">
        <ul>
          <li><a href="/home">Home</a></li>
          <li><a href="/products">Products</a></li>
          <li><a href="/about">About</a></li>
        </ul>
      </nav>
      <div class="hamburger-menu-icon" onclick="toggleMobileMenu(this)">
        <div class="bar1"></div>
        <div class="bar2"></div>
        <div class="bar3"></div>
      </div>
    </header>

    <main>
      <section class="main-section container">
        <h2>Main Content</h2>
        <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit.</p>
      </section>
      <aside class="sidebar container">
        <h2>Sidebar</h2>
        <ul>
          <li>Item 1</li>
          <li>Item 2</li>
          <li>Item 3</li>
        </ul>
      </aside>
    </main>

    <footer class="footer">
      <p>IronHack pre-work excercise</p>
    </footer>
    <script src="index.js"></script>
  </body>
</html>
```

## Estilos CSS (index.css)

Se creó un archivo `index.css` para definir los estilos del diseño responsive utilizando Flexbox.

### Layout

Se ajusto los 3 principales elementos para que ocuparan minimamente la pantalla completa **Header**, **Main** y **Footer**

```css
.header {
  height: 50px;
}
main {
  min-height: calc(100vh - 120px);
}
.footer {
  height: 70px;
}
```

### Header

Se utilizó Flexbox para alinear horizontalmente y verticalmente el logotipo y el menú de navegación

```css
.header {
  padding: 0 20px;
  background-color: #1976d2;
  height: 50px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}
```

### Navigation

Se utilizó Flexbox para alinear horizontalmente los elementos del menú, lo importante a destacar aqui es que el menu de navegación es el mismo elemento, tanto en mobile como en desktop y solo se ajustan estilos:

```html
<header class="header">
  <div class="logo">
    <a href="/">My Logo</a>
  </div>
  <nav class="menu">
    <ul>
      <li><a href="/home">Home</a></li>
      <li><a href="/products">Products</a></li>
      <li><a href="/about">About</a></li>
    </ul>
  </nav>
  <div class="hamburger-menu-icon" onclick="toggleMobileMenu(this)">
    <div class="bar1"></div>
    <div class="bar2"></div>
    <div class="bar3"></div>
  </div>
</header>
```

### Main Content y Sidebar

Se creó un diseño flexible que ajusta el espacio disponible entre el contenido principal y la barra lateral:

```css
main {
  display: flex;
  flex-direction: column;
  min-height: calc(100vh - 120px);
}

/* main content */
.main-section {
  flex: 1;
  flex-grow: 3;
  margin-right: 20px;
  min-width: 200px;
}

/* Sidebar */
.sidebar {
  flex: 1;
  background-color: #f1f1f1;
  padding: 20px;
  min-width: 200px;
}
```

### Footer

Se utilizó Flexbox para alinear horizontalmente y verticalmente el contenido dentro del pie de página:

```css
footer {
  height: 70px;
  background-color: #1976d2;
  color: #fff;
  text-align: center;
  padding: 10px;
}
```

### Media Queries

Debido a que se hizo bajo el enfoque mobile first, solo se utilizaron media queries para definir diferentes configuraciones a partir de un tamaños de pantalla de un ancho minimo de 768 píxeles, el menu se ajusta para desktop ya que es el mismo elemento que mobile, se ajusta tambien el acomodo de los contenedores principales y algunos elementos se ocultan, como el menú de hamburguesa:

```css
@media only screen and (min-width: 768px) {
  main {
    flex-direction: row;
  }

  /* remove mobile menu style */
  .menu {
    display: flex;
    position: relative;
    top: initial;
    left: initial;
    width: auto;
    height: auto;
    background-color: transparent;
  }

  .menu ul {
    display: flex;
  }

  .menu li {
    margin-bottom: 0;
  }

  .hamburger-menu-icon {
    display: none;
  }
}
```

## Pruebas y Ajustes

Se realizaron pruebas en diferentes tamaños de pantalla y dispositivos utilizando las herramientas de desarrollo del navegador para asegurar la adaptabilidad y la respuesta del diseño. Se realizaron los ajustes necesarios para optimizar la experiencia del usuario en diferentes dispositivos.

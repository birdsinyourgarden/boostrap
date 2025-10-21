# Bootstrap 5

## Índice
1. Introducción a Bootstrap 5
2. Sistema de Grid
3. Utilidades y Componentes
4. Personalización y Temas
5. JavaScript y Componentes Interactivos

---

## 1. Introducción a Bootstrap 5

Bootstrap 5 es el framework CSS más popular para desarrollar sitios web responsivos y mobile-first. Fue lanzado en mayo de 2021 y representa una evolución significativa respecto a versiones anteriores.

### Novedades principales de Bootstrap 5

Bootstrap 5 introdujo cambios importantes que modernizaron el framework. La eliminación de jQuery como dependencia fue uno de los cambios más significativos, lo que resultó en un framework más ligero y rápido. Ahora utiliza JavaScript vanilla puro, lo que mejora el rendimiento y reduce el tamaño del bundle final.

Otra mejora importante fue la actualización del sistema de grid, que ahora incluye una nueva breakpoint XXL para pantallas extra grandes. El sistema de utilidades se expandió considerablemente, ofreciendo clases para casi cualquier necesidad de estilo sin necesidad de escribir CSS personalizado.

La documentación fue completamente renovada, haciéndola más clara y accesible. Se añadieron nuevos componentes como offcanvas y se mejoraron los existentes. El sistema de formularios fue rediseñado para ofrecer mejor accesibilidad y personalización.

### Instalación y configuración

Existen varias formas de integrar Bootstrap 5 en tu proyecto. La forma más rápida es mediante CDN, incluyendo los archivos CSS y JavaScript directamente en tu HTML:

```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mi Proyecto Bootstrap</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css" rel="stylesheet">
</head>
<body>
    <!-- Tu contenido aquí -->
    
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/js/bootstrap.bundle.min.js"></script>
</body>
</html>
```

Para proyectos más complejos, puedes instalar Bootstrap mediante npm:

```bash
npm install bootstrap@5.3.0
```

Si deseas personalizar Bootstrap usando Sass, necesitarás instalar las dependencias y configurar tu entorno de compilación. Esto te permite modificar variables, crear temas personalizados y compilar solo los componentes que necesitas.

### Estructura básica de un documento

Todo documento Bootstrap debe incluir el meta tag viewport para asegurar el comportamiento responsivo correcto. La etiqueta DOCTYPE debe ser HTML5, y se recomienda incluir el atributo lang en la etiqueta html para mejorar la accesibilidad.

---

## 2. Sistema de Grid

El sistema de grid de Bootstrap es una de sus características más poderosas. Permite crear layouts complejos y responsivos utilizando un sistema de 12 columnas basado en flexbox.

### Conceptos fundamentales

El sistema de grid se basa en tres elementos principales: containers, rows y columns. Los containers proporcionan un ancho máximo y centrado horizontal. Las rows crean grupos horizontales de columnas y las columns contienen el contenido.

Bootstrap 5 utiliza flexbox para el grid, lo que proporciona un control más preciso sobre el alineamiento, el espaciado y la distribución del contenido. El sistema es completamente responsivo y se adapta automáticamente a diferentes tamaños de pantalla.

### Containers

Existen tres tipos de containers en Bootstrap 5. El container estándar tiene anchos máximos predefinidos que cambian en cada breakpoint. El container-fluid ocupa el 100% del ancho disponible en todos los tamaños de pantalla. Los containers responsivos como container-md o container-lg se comportan como fluid hasta alcanzar su breakpoint específico.

```html
<div class="container">
    <!-- Contenido con ancho máximo -->
</div>

<div class="container-fluid">
    <!-- Contenido a ancho completo -->
</div>

<div class="container-md">
    <!-- Fluid en móviles, container fijo desde md en adelante -->
</div>
```

### Breakpoints

Bootstrap 5 define seis breakpoints principales que determinan cómo se comporta el contenido en diferentes dispositivos:

- **xs** (extra small): < 576px - Teléfonos en vertical
- **sm** (small): ≥ 576px - Teléfonos en horizontal
- **md** (medium): ≥ 768px - Tablets
- **lg** (large): ≥ 992px - Escritorio estándar
- **xl** (extra large): ≥ 1200px - Escritorio grande
- **xxl** (extra extra large): ≥ 1400px - Pantallas muy grandes

### Sistema de columnas

El grid se divide en 12 columnas. Puedes crear layouts especificando cuántas columnas debe ocupar cada elemento. Las clases siguen el patrón `col-{breakpoint}-{number}`.

```html
<div class="container">
    <div class="row">
        <div class="col-md-8">
            Columna principal (8 columnas en tablets+)
        </div>
        <div class="col-md-4">
            Sidebar (4 columnas en tablets+)
        </div>
    </div>
</div>
```

Si no especificas el número de columnas, estas se distribuyen uniformemente:

```html
<div class="row">
    <div class="col">Columna automática</div>
    <div class="col">Columna automática</div>
    <div class="col">Columna automática</div>
</div>
```

### Alineación y ordenamiento

Flexbox permite un control preciso sobre la alineación de columnas. Puedes alinear columnas vertical y horizontalmente usando clases de utilidad.

Para alineación vertical en la row:
```html
<div class="row align-items-start">...</div>
<div class="row align-items-center">...</div>
<div class="row align-items-end">...</div>
```

Para alineación horizontal:
```html
<div class="row justify-content-start">...</div>
<div class="row justify-content-center">...</div>
<div class="row justify-content-end">...</div>
<div class="row justify-content-between">...</div>
<div class="row justify-content-around">...</div>
```

Puedes reordenar columnas visualmente sin cambiar el HTML usando las clases `order-`:

```html
<div class="row">
    <div class="col order-3">Primero en el código, tercero visualmente</div>
    <div class="col order-1">Segundo en el código, primero visualmente</div>
    <div class="col order-2">Tercero en el código, segundo visualmente</div>
</div>
```

### Gutters y espaciado

Los gutters son los espacios horizontales entre columnas. Por defecto, Bootstrap aplica gutters de 1.5rem (24px). Puedes controlar los gutters con las clases `g-`:

```html
<!-- Sin gutters -->
<div class="row g-0">...</div>

<!-- Gutters personalizados -->
<div class="row g-3">...</div>
<div class="row g-5">...</div>

<!-- Gutters solo horizontales o verticales -->
<div class="row gx-4">...</div>
<div class="row gy-3">...</div>
```

### Nesting (anidamiento)

Puedes anidar grids dentro de otros grids. Cada nivel anidado obtiene su propio conjunto de 12 columnas:

```html
<div class="row">
    <div class="col-md-8">
        <div class="row">
            <div class="col-md-6">Columna anidada</div>
            <div class="col-md-6">Columna anidada</div>
        </div>
    </div>
    <div class="col-md-4">Sidebar</div>
</div>
```

---

## 3. Utilidades y Componentes

Bootstrap 5 ofrece un sistema extenso de clases de utilidad que cubren prácticamente todas las necesidades de estilo común, además de componentes prediseñados listos para usar.

### Tipografía

Bootstrap proporciona clases para manejar todo tipo de texto. Los encabezados pueden usarse como elementos HTML o como clases para aplicar estilos de encabezado a cualquier elemento:

```html
<h1>Encabezado H1</h1>
<p class="h1">Párrafo con estilo de H1</p>

<p class="display-1">Display heading 1</p>
<p class="lead">Texto destacado con mayor tamaño</p>
<p class="text-muted">Texto con color atenuado</p>
```

Las clases de utilidad de texto incluyen alineación, transformación, peso y estilo:

```html
<p class="text-start">Texto alineado a la izquierda</p>
<p class="text-center">Texto centrado</p>
<p class="text-end">Texto alineado a la derecha</p>

<p class="text-lowercase">texto en minúsculas</p>
<p class="text-uppercase">TEXTO EN MAYÚSCULAS</p>
<p class="text-capitalize">texto capitalizado</p>

<p class="fw-bold">Texto en negrita</p>
<p class="fw-normal">Texto normal</p>
<p class="fst-italic">Texto en cursiva</p>
```

### Colores

Bootstrap define un conjunto de colores semánticos que mantienen consistencia en todo el framework. Estos colores pueden aplicarse a texto, fondos y bordes:

```html
<!-- Colores de texto -->
<p class="text-primary">Texto primario</p>
<p class="text-secondary">Texto secundario</p>
<p class="text-success">Texto de éxito</p>
<p class="text-danger">Texto de peligro</p>
<p class="text-warning">Texto de advertencia</p>
<p class="text-info">Texto informativo</p>

<!-- Colores de fondo -->
<div class="bg-primary text-white">Fondo primario</div>
<div class="bg-success text-white">Fondo de éxito</div>

<!-- Colores de fondo sutiles (Bootstrap 5.2+) -->
<div class="bg-primary-subtle">Fondo primario sutil</div>
```

### Spacing (espaciado)

El sistema de espaciado de Bootstrap es uno de los más utilizados. Sigue el patrón `{property}{sides}-{size}` o `{property}{sides}-{breakpoint}-{size}`:

- **Property**: m (margin) o p (padding)
- **Sides**: t (top), b (bottom), s (start/left), e (end/right), x (horizontal), y (vertical), o vacío (todos los lados)
- **Size**: 0 a 5, o auto

```html
<div class="mt-3">Margen superior de 1rem</div>
<div class="p-4">Padding de 1.5rem en todos los lados</div>
<div class="mx-auto">Márgenes horizontales automáticos (centrado)</div>
<div class="py-2 px-4">Padding vertical de 0.5rem y horizontal de 1.5rem</div>

<!-- Responsivo -->
<div class="mt-2 mt-md-4">Margen superior que aumenta en tablets+</div>
```

### Display y visibilidad

Controla cómo se muestran los elementos y su visibilidad en diferentes breakpoints:

```html
<!-- Display -->
<div class="d-block">Display block</div>
<div class="d-inline">Display inline</div>
<div class="d-flex">Display flex</div>
<div class="d-grid">Display grid</div>
<div class="d-none">Elemento oculto</div>

<!-- Display responsivo -->
<div class="d-none d-md-block">Oculto en móviles, visible desde tablets+</div>
<div class="d-block d-lg-none">Visible hasta lg, oculto en pantallas grandes</div>
```

### Flexbox

Bootstrap incluye clases de utilidad para trabajar con flexbox de manera sencilla:

```html
<div class="d-flex justify-content-between">
    <div>Item 1</div>
    <div>Item 2</div>
</div>

<div class="d-flex align-items-center" style="height: 200px;">
    <div>Centrado verticalmente</div>
</div>

<div class="d-flex flex-column">
    <div>Item en columna 1</div>
    <div>Item en columna 2</div>
</div>

<!-- Flex responsivo -->
<div class="d-flex flex-column flex-md-row">
    Columna en móviles, fila en tablets+
</div>
```

### Borders y Radius

Aplica bordes y esquinas redondeadas fácilmente:

```html
<!-- Bordes -->
<div class="border">Borde completo</div>
<div class="border-top">Solo borde superior</div>
<div class="border-0">Sin bordes</div>
<div class="border border-primary">Borde con color primario</div>

<!-- Border radius -->
<img src="..." class="rounded">
<img src="..." class="rounded-circle">
<img src="..." class="rounded-pill">
<div class="rounded-top">Solo esquinas superiores redondeadas</div>
```

### Shadows

Añade sombras para crear profundidad:

```html
<div class="shadow-sm">Sombra pequeña</div>
<div class="shadow">Sombra regular</div>
<div class="shadow-lg">Sombra grande</div>
```

### Componentes principales

#### Navbar

El navbar es uno de los componentes más utilizados para crear barras de navegación responsivas:

```html
<nav class="navbar navbar-expand-lg navbar-light bg-light">
    <div class="container-fluid">
        <a class="navbar-brand" href="#">Logo</a>
        <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav">
            <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarNav">
            <ul class="navbar-nav ms-auto">
                <li class="nav-item">
                    <a class="nav-link active" href="#">Inicio</a>
                </li>
                <li class="nav-item">
                    <a class="nav-link" href="#">Servicios</a>
                </li>
                <li class="nav-item">
                    <a class="nav-link" href="#">Contacto</a>
                </li>
            </ul>
        </div>
    </div>
</nav>
```

#### Cards

Las cards son contenedores flexibles y extensibles para mostrar contenido:

```html
<div class="card" style="width: 18rem;">
    <img src="..." class="card-img-top" alt="...">
    <div class="card-body">
        <h5 class="card-title">Título de la card</h5>
        <p class="card-text">Descripción del contenido de la card.</p>
        <a href="#" class="btn btn-primary">Ver más</a>
    </div>
</div>
```

#### Buttons

Bootstrap ofrece múltiples estilos de botones:

```html
<button type="button" class="btn btn-primary">Primario</button>
<button type="button" class="btn btn-secondary">Secundario</button>
<button type="button" class="btn btn-success">Éxito</button>
<button type="button" class="btn btn-danger">Peligro</button>

<!-- Botones outline -->
<button type="button" class="btn btn-outline-primary">Outline Primario</button>

<!-- Tamaños -->
<button type="button" class="btn btn-primary btn-lg">Grande</button>
<button type="button" class="btn btn-primary btn-sm">Pequeño</button>

<!-- Estados -->
<button type="button" class="btn btn-primary" disabled>Deshabilitado</button>
```

#### Formularios

Bootstrap 5 mejoró significativamente los controles de formulario:

```html
<form>
    <div class="mb-3">
        <label for="email" class="form-label">Email</label>
        <input type="email" class="form-control" id="email" placeholder="nombre@ejemplo.com">
    </div>
    
    <div class="mb-3">
        <label for="password" class="form-label">Contraseña</label>
        <input type="password" class="form-control" id="password">
    </div>
    
    <div class="mb-3">
        <label for="select" class="form-label">Selecciona una opción</label>
        <select class="form-select" id="select">
            <option selected>Elige...</option>
            <option value="1">Opción 1</option>
            <option value="2">Opción 2</option>
        </select>
    </div>
    
    <div class="mb-3 form-check">
        <input type="checkbox" class="form-check-input" id="check">
        <label class="form-check-label" for="check">
            Acepto los términos
        </label>
    </div>
    
    <button type="submit" class="btn btn-primary">Enviar</button>
</form>
```

#### Modales

Los modales son ventanas emergentes que se superponen al contenido:

```html
<!-- Botón para activar el modal -->
<button type="button" class="btn btn-primary" data-bs-toggle="modal" data-bs-target="#miModal">
    Abrir Modal
</button>

<!-- Modal -->
<div class="modal fade" id="miModal" tabindex="-1">
    <div class="modal-dialog">
        <div class="modal-content">
            <div class="modal-header">
                <h5 class="modal-title">Título del Modal</h5>
                <button type="button" class="btn-close" data-bs-dismiss="modal"></button>
            </div>
            <div class="modal-body">
                <p>Contenido del modal...</p>
            </div>
            <div class="modal-footer">
                <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Cerrar</button>
                <button type="button" class="btn btn-primary">Guardar</button>
            </div>
        </div>
    </div>
</div>
```

#### Alerts

Las alertas muestran mensajes de retroalimentación al usuario:

```html
<div class="alert alert-primary" role="alert">
    Esta es una alerta primaria
</div>

<div class="alert alert-success alert-dismissible fade show" role="alert">
    Operación exitosa!
    <button type="button" class="btn-close" data-bs-dismiss="alert"></button>
</div>
```

---

## 4. Personalización y Temas

Una de las ventajas de Bootstrap es su capacidad de personalización mediante Sass.

### Variables de Sass

Bootstrap define cientos de variables que controlan colores, espaciado, tipografía y más. Para personalizarlo, crea tu propio archivo Sass:

```scss
// custom.scss

// Sobrescribe variables antes de importar Bootstrap
$primary: #0074d9;
$secondary: #6c757d;
$success: #2ecc40;
$danger: #ff4136;

$font-family-sans-serif: "Roboto", system-ui, -apple-system, sans-serif;
$font-size-base: 1rem;
$line-height-base: 1.6;

// Importa Bootstrap
@import "node_modules/bootstrap/scss/bootstrap";

// Tu CSS personalizado aquí
.mi-clase-custom {
    background-color: $primary;
    padding: $spacer * 2;
}
```

### Temas personalizados

Puedes crear temas completos modificando el mapa de colores de Bootstrap:

```scss
$custom-colors: (
  "custom-color": #900c3f
);

$theme-colors: map-merge($theme-colors, $custom-colors);

@import "node_modules/bootstrap/scss/bootstrap";
```

### Compilación selectiva

Para reducir el tamaño del archivo final, puedes importar solo los componentes que necesitas:

```scss
// Importa solo funciones y variables requeridas
@import "node_modules/bootstrap/scss/functions";
@import "node_modules/bootstrap/scss/variables";
@import "node_modules/bootstrap/scss/mixins";

// Importa componentes específicos
@import "node_modules/bootstrap/scss/root";
@import "node_modules/bootstrap/scss/reboot";
@import "node_modules/bootstrap/scss/grid";
@import "node_modules/bootstrap/scss/utilities";
@import "node_modules/bootstrap/scss/buttons";
@import "node_modules/bootstrap/scss/navbar";
```

---

## 5. JavaScript y Componentes Interactivos

Bootstrap 5 incluye JavaScript para componentes interactivos sin necesidad de jQuery.

### Inicialización de componentes

Puedes inicializar componentes mediante atributos data o JavaScript:

```html
<!-- Mediante atributos data -->
<button type="button" class="btn btn-primary" data-bs-toggle="tooltip" data-bs-placement="top" title="Tooltip">
    Hover me
</button>

<script>
// Inicialización mediante JavaScript
const tooltipTriggerList = document.querySelectorAll('[data-bs-toggle="tooltip"]')
const tooltipList = [...tooltipTriggerList].map(tooltipTriggerEl => new bootstrap.Tooltip(tooltipTriggerEl))
</script>
```

### Componentes JavaScript principales

#### Tooltips

Los tooltips deben inicializarse manualmente:

```javascript
const tooltipTriggerList = document.querySelectorAll('[data-bs-toggle="tooltip"]')
const tooltipList = [...tooltipTriggerList].map(el => new bootstrap.Tooltip(el))
```

#### Popovers

Similar a los tooltips pero con más contenido:

```html
<button type="button" class="btn btn-lg btn-danger" 
        data-bs-toggle="popover" 
        data-bs-title="Título del Popover"
        data-bs-content="Contenido del popover aquí.">
    Click para popover
</button>

<script>
const popoverTriggerList = document.querySelectorAll('[data-bs-toggle="popover"]')
const popoverList = [...popoverTriggerList].map(el => new bootstrap.Popover(el))
</script>
```

#### Collapse

Permite mostrar y ocultar contenido:

```html
<button class="btn btn-primary" type="button" data-bs-toggle="collapse" data-bs-target="#collapseExample">
    Toggle contenido
</button>

<div class="collapse" id="collapseExample">
    <div class="card card-body">
        Contenido colapsable
    </div>
</div>
```

#### Carousel

Crea sliders de imágenes o contenido:

```html
<div id="carouselExample" class="carousel slide" data-bs-ride="carousel">
    <div class="carousel-inner">
        <div class="carousel-item active">
            <img src="..." class="d-block w-100" alt="...">
        </div>
        <div class="carousel-item">
            <img src="..." class="d-block w-100" alt="...">
        </div>
    </div>
    <button class="carousel-control-prev" type="button" data-bs-target="#carouselExample" data-bs-slide="prev">
        <span class="carousel-control-prev-icon"></span>
    </button>
    <button class="carousel-control-next" type="button" data-bs-target="#carouselExample" data-bs-slide="next">
        <span class="carousel-control-next-icon"></span>
    </button>
</div>
```

#### Offcanvas

Nuevo en Bootstrap 5, crea sidebars deslizantes:

```html
<button class="btn btn-primary" type="button" data-bs-toggle="offcanvas" data-bs-target="#offcanvasExample">
    Abrir offcanvas
</button>

<div class="offcanvas offcanvas-start" tabindex="-1" id="offcanvasExample">
    <div class="offcanvas-header">
        <h5 class="offcanvas-title">Título</h5>
        <button type="button" class="btn-close" data-bs-dismiss="offcanvas"></button>
    </div>
    <div class="offcanvas-body">
        Contenido del sidebar...
    </div>
</div>
```

### API de JavaScript

Puedes controlar componentes mediante JavaScript:

```javascript
// Modal
const myModal = new bootstrap.Modal(document.getElementById('myModal'))
myModal.show()
myModal.hide()

// Toast
const toastElList = document.querySelectorAll('.toast')
const toastList = [...toastElList].map(toastEl => new bootstrap.Toast(toastEl))
toastList.forEach(toast => toast.show())

// Eventos
const myModalEl = document.getElementById('myModal')
myModalEl.addEventListener('shown.bs.modal', event => {
    console.log('Modal se ha mostrado')
})
```

### Validación de formularios

Bootstrap proporciona estilos de validación personalizados:

```html
<form class="needs-validation" novalidate>
    <div class="mb-3">
        <label for="validationCustom01" class="form-label">Nombre</label>
        <input type="text" class="form-control" id="validationCustom01" required>
        <div class="valid-feedback">¡Se ve bien!</div>
        <div class="invalid-feedback">Por favor ingresa un nombre.</div>
    </div>
    <button class="btn btn-primary" type="submit">Enviar</button>
</form>

<script>
const forms = document.querySelectorAll('.needs-validation')
Array.from(forms).forEach(form => {
    form.addEventListener('submit', event => {
        if (!form.checkValidity()) {
            event.preventDefault()
            event.stopPropagation()
        }
        form.classList.add('was-validated')
    }, false)
})
</script>
```

## Ejercicio 1: Crear una página con un navbar

**Enunciado:** Crea una página web que tenga un navbar de Bootstrap. El navbar debe:

* Tener el nombre de la página a la izquierda.
* Tener tres enlaces a la derecha: "Inicio", "Servicios" y "Contacto".
* Ser responsive y colapsar en un botón de menú en pantallas pequeñas.

---

## Ejercicio 2: Botones con estilos

**Enunciado:** Crea una sección con cinco botones diferentes usando clases de Bootstrap:

* `btn-primary`
* `btn-success`
* `btn-danger`
* `btn-warning`
* `btn-info`

Asegúrate de que los botones tengan un margen entre ellos y se vean alineados horizontalmente.

---

## Ejercicio 3: Tarjetas (Cards)

**Enunciado:** Crea tres tarjetas (cards) con Bootstrap que contengan:

* Una imagen en la parte superior.
* Un título.
* Una descripción breve.
* Un botón que diga "Más información".

Organiza las tarjetas en fila en pantallas grandes y apiladas en pantallas pequeñas usando el sistema de grid de Bootstrap.

## Ejercicio 4: Formulario responsive

**Enunciado:** Crea un formulario de contacto que contenga:

* Nombre completo (input de texto)
* Correo electrónico (input de email)
* Mensaje (textarea)
* Botón de enviar

Haz que el formulario se vea bien en móviles y en escritorio, usando clases de `form-control` y `row` de Bootstrap para organizar los campos.

---

## Ejercicio 5: Sistema de Grid

**Enunciado:** Crea una sección con 4 columnas de igual tamaño en pantallas grandes.

* En pantallas medianas, que se reduzcan a 2 columnas.
* En pantallas pequeñas, que se apilen en 1 columna.
* Cada columna debe contener un icono y un título.

---

## Ejercicio 6: Carousel de imágenes

**Enunciado:** Crea un carrusel (carousel) con 3 imágenes.

* Cada slide debe tener un texto superpuesto (puede ser un título o frase corta).
* El carrusel debe incluir indicadores y controles para avanzar y retroceder.

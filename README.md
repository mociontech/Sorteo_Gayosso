# Sorteo_Gayosso
Sistema de sorteo interactivo con animaciones para pantalla LED 4K. Sortea números del 017001 al 017690 sin repetición.

## Descripción

Aplicación web HTML pura que permite realizar sorteos de folios numerados con animaciones visuales atractivas y efectos de tensión para crear una experiencia emocionante para los participantes.

## Características

- **Diseño responsivo**: Optimizado para pantallas LED de 4K (3840x2160px)
- **Sin dependencias**: HTML, CSS y JavaScript puro, sin frameworks
- **Funcionamiento offline**: No requiere conexión a internet
- **Sorteo sin repetición**: Los números sorteados no se repiten
- **Animaciones fluidas**: Transiciones suaves y efecto de "rodado" de números
- **Rango de folios**: 017001 al 017690 (690 números únicos)
- **Reinicio fácil**: Botón de reset para volver a comenzar

## Estructura del Proyecto

\`\`\`
sorteo-gayosso/
├── sorteo.html              # Archivo principal
└── images/                  # Carpeta de recursos visuales
    ├── particulas-doradas.png
    ├── copos-fondo.png
    ├── marco.png
    ├── logo-gayosso.png
    └── BIENVENIDOS.png
\`\`\`

## Requisitos

- Navegador web moderno (Chrome, Firefox, Edge, Safari)
- No requiere servidor web
- No requiere conexión a internet

## Instalación

1. **Descargar el proyecto completo**
   - Descarga todos los archivos del proyecto

2. **Organizar la estructura de carpetas**
   \`\`\`
   sorteo.html
   images/
     ├── particulas-doradas.png
     ├── copos-fondo.png
     ├── marco.png
     ├── logo-gayosso.png
     └── BIENVENIDOS.png
   \`\`\`

3. **Verificar las imágenes**
   - Asegúrate de que los nombres de las imágenes coincidan exactamente
   - Las extensiones deben ser `.png`
   - Todos los archivos deben estar en la carpeta `images/`

## Uso

### Inicio del Sorteo

1. Abre el archivo `sorteo.html` en un navegador web
2. Se mostrará la pantalla de bienvenida con:
   - Logo de Gayosso 150 años
   - Texto "BIENVENIDOS"
   - Decoración navideña
   - Botón "Comenzar"

### Durante el Sorteo

1. Haz clic en **"Comenzar"** para iniciar el sorteo
2. La pantalla cambiará mostrando:
   - Logo de Gayosso (posición superior)
   - Mensaje: "Si el número que ves es el tuyo ¡Eres ganador!"
   - Número ganador en grande
   - Botón "Siguiente"

3. Haz clic en **"Siguiente"** para sortear el próximo número
   - Se mostrará una animación de "rodado" de números
   - El botón se deshabilitará durante la animación
   - Después de 1.5 segundos se revelará el número ganador

4. Repite el paso 3 hasta sortear todos los números necesarios

### Reiniciar el Sorteo

- En cualquier momento durante el sorteo, puedes hacer clic en el botón **"Reiniciar"** (esquina inferior izquierda)
- Esto regresará a la pantalla de bienvenida y reiniciará todos los números disponibles

## Especificaciones Técnicas

### Dimensiones

- **Canvas total**: 3840px × 2160px
- **Marco decorativo**: 3840px × 1326px
- **Logo Gayosso**: 818px × 136px
- **Texto BIENVENIDOS**: 2015px × 436px
- **Partículas doradas**: 4600px × 2120px (extendidas)
- **Copos de fondo**: 3840px × 958px

### Posiciones (Primera Pantalla)

- **Logo Gayosso**: top: 759px, left: 1511px
- **Texto BIENVENIDOS**: top: 847px, left: 912px
- **Botón Comenzar**: top: 1649px, left: 1565px

### Posiciones (Segunda Pantalla - Sorteo)

- **Logo Gayosso**: top: 559px, left: 1511px
- **Mensaje ganador**: top: 850px
- **Número ganador**: top: 1050px
- **Botón Siguiente**: top: 1649px, left: 1565px
- **Botón Reiniciar**: bottom: 40px, left: 40px

### Animaciones

1. **Transición de pantallas**: 0.8s fade in/out
2. **Rodado de números**: 1.5s (15 iteraciones a 100ms)
3. **Movimiento de logo**: 0.8s ease
4. **Hover en botones**: 0.3s

### Rango de Folios

- **Inicio**: 017001
- **Fin**: 017690
- **Total**: 690 números únicos
- **Formato**: 6 dígitos con ceros a la izquierda

## Paleta de Colores

- **Fondo**: Negro (#000000)
- **Dorado principal**: #C9A961
- **Dorado hover**: #B89851
- **Texto**: Blanco (#FFFFFF)

## Tipografía

- **Familia**: Arial, sans-serif
- **Tamaños**:
  - Mensaje ganador: 48px
  - Número ganador: 280px (peso 700)
  - Botón principal: 42px (peso 600)
  - Botón reiniciar: 18px (peso 500)

## Funcionalidades Técnicas

### Algoritmo de Sorteo

\`\`\`javascript
// Fisher-Yates shuffle para garantizar números únicos sin repetición
function shuffleArray(array) {
  for (let i = array.length - 1; i > 0; i--) {
    const j = Math.floor(Math.random() * (i + 1));
    [array[i], array[j]] = [array[j], array[i]];
  }
  return array;
}
\`\`\`

### Animación de Tensión

- Muestra 15 números aleatorios rápidamente
- Cada número se muestra durante 100ms
- Crea efecto de "máquina tragamonedas"
- El último número mostrado es el ganador real

### Prevención de Clicks Múltiples

- Los botones se deshabilitan durante las animaciones
- Previene errores por clicks rápidos
- Se rehabilitan automáticamente al terminar

## Solución de Problemas

### Las imágenes no se muestran

1. Verifica que la carpeta `images/` esté al mismo nivel que `sorteo.html`
2. Confirma que los nombres de los archivos sean exactos (incluyendo mayúsculas/minúsculas)
3. Asegúrate de que las extensiones sean `.png`

### El diseño se ve desalineado

1. Abre el archivo en pantalla completa (F11 en la mayoría de navegadores)
2. Verifica que la resolución de tu pantalla sea compatible
3. Para pantallas LED, asegúrate de que estén configuradas en 3840×2160

### Los números se repiten

- Usa el botón "Reiniciar" para resetear completamente el sorteo
- Esto regenerará la lista de números disponibles

### La animación va muy rápida/lenta

Puedes ajustar la velocidad en el código:
\`\`\`javascript
// Busca estas líneas en sorteo.html
setTimeout(() => { ... }, 100);  // Cambia 100 (ms) por el valor deseado
\`\`\`

## Personalización

### Cambiar el rango de números

Modifica estas variables en el código:
\`\`\`javascript
const MIN_NUMBER = 17001;  // Número inicial
const MAX_NUMBER = 17690;  // Número final
\`\`\`

### Ajustar posiciones

Busca las clases CSS correspondientes y modifica los valores `top` y `left`:
\`\`\`css
.logo-gayosso {
  top: 759px;
  left: 1511px;
}
\`\`\`

### Modificar colores

Busca las variables de color en los estilos CSS:
\`\`\`css
background: linear-gradient(135deg, #C9A961, #B89851);
\`\`\`

## Compatibilidad

- **Chrome**: ✓ Compatible
- **Firefox**: ✓ Compatible
- **Edge**: ✓ Compatible
- **Safari**: ✓ Compatible
- **Opera**: ✓ Compatible

## Notas de Desarrollo

- Desarrollado con HTML5, CSS3 y JavaScript ES6
- No utiliza librerías externas
- Optimizado para rendimiento en pantallas LED
- Utiliza `position: absolute` para posicionamiento preciso
- Animaciones con CSS transitions y keyframes

## Créditos

- **Cliente**: Gayosso 150 Años
- **Diseño**: Basado en especificaciones de Figma
- **Desarrollo**: Sistema de sorteo interactivo
- **Desarrollador**: Marco Flores

---

Para soporte o consultas, contacta al equipo de desarrollo.

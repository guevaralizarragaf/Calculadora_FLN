# Calculadora de Comisiones — Fortalecernos SAC

Sitio estático de una sola página (`index.html`, sin dependencias de backend) para calcular el
"Ganado" mensual del equipo comercial: sueldo básico + comisión variable calculada por producto.

## Cómo publicarlo gratis en GitHub Pages

1. Crea un repositorio nuevo en GitHub (por ejemplo `comisiones-fortalecernos`). Puede ser público
   o privado (Pages funciona en ambos si tienes plan que lo permita; en repos públicos siempre es gratis).
2. Sube estos dos archivos a la raíz del repositorio: `index.html` y `README.md`.
   - Desde la web de GitHub: botón **Add file → Upload files**, arrastra `index.html` y confirma el commit.
   - O desde tu computadora:
     ```bash
     git init
     git add index.html README.md
     git commit -m "Calculadora de comisiones"
     git branch -M main
     git remote add origin https://github.com/TU_USUARIO/comisiones-fortalecernos.git
     git push -u origin main
     ```
3. En el repositorio, ve a **Settings → Pages**.
4. En "Build and deployment", selecciona **Deploy from a branch**, rama `main`, carpeta `/ (root)`, y guarda.
5. Espera 1-2 minutos. GitHub te dará una URL como:
   `https://TU_USUARIO.github.io/comisiones-fortalecernos/`
6. Comparte esa URL con el equipo. Cada vez que subas un nuevo commit a `main`, la página se actualiza sola.

## Notas sobre el cálculo

- **Cumplimiento** = Venta ÷ Cuota, por producto.
- La comisión de un producto solo se paga si el cumplimiento es **70% o más**.
- Comisión del producto = Mix% × Comisión variable (monto ingresado arriba) × Cumplimiento.
- En **VR CAPTURA** el cumplimiento tiene tope de 100% (aunque venda más, no se paga de más por ese tope).
- En el resto de productos no hay tope: si el cumplimiento supera 100%, la comisión sigue creciendo.
- **Bonos por unidad adicional**: por cada unidad vendida por encima de la cuota se suma un monto fijo:
  - OSS MONO + OSS LLAA: S/10 por unidad extra.
  - OPP BASE: S/5 por unidad extra.
  - VR LLAA BASE: S/10 por unidad extra.
- **NPS de venta**: si el NPS logrado es ≥ 70%, se suman S/50.
- **MIS IN**: si la venta alcanza la cuota indicada, se suman S/50.
- Los datos ingresados se guardan automáticamente en el navegador (localStorage), así que si
  recargan la página no se pierden. El botón "Reiniciar datos" los borra.

## Personalización rápida

Los productos, porcentajes de mix y condiciones están definidos al inicio del `<script>` en
`index.html`, dentro del arreglo `PRODUCTS`. Puedes editar nombres, `mix`, `bono` (monto por unidad
extra) o el texto de `condicion` directamente ahí sin tocar el resto del código.

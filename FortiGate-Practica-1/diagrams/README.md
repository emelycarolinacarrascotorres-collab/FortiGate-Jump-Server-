# Diagramas

Los diagramas están escritos en Mermaid y se renderizan directamente en GitHub dentro de [`docs/02-arquitectura.md`](../docs/02-arquitectura.md) y del [`README.md`](../README.md).

Para exportarlos a PNG/SVG (si hace falta): `npm i -g @mermaid-js/mermaid-cli` y `mmdc -i bloque.mmd -o topologia-general.png`, copiando cada bloque `mermaid` a un archivo `.mmd`. No se incluyen PNG generados para no duplicar el contenido.

Tres diagramas: topología lógica, flujo de tráfico (secuencia) y control de acceso por capas.

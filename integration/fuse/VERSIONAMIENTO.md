[ **[Volver al Menú Principal](MAIN.md)** ]


Acorde al lineamiento transversal del CedEx de Desarrollo, se trabaja con el modelo de ramas y versionado semantico definido:

- [Ref: Branching](https://github.com/UniandesDSIT/coding-guidelines/blob/master/versioning/BRANCHES.md)

Lo recomendable es manejar N ramas en git con todo el código fuente y los archivos .properties con la siguiente estructura:
- **Rama-Master**: En esta rama estaría el código de las versiones certificadas y entregadas a la universidad, segmentadas por Tags, dependiendo la version.
- **Rama-Staying**: Esta rama deberá contener la versión a certificar para paso a producción, deberá ser similar a master pero si se encuentran issues o bugs en la etapa de certificación las correcciones nacen de esta y no de master directamente.
- **Rama-Develop-Sprint-X**: Apoyados en la metodología SCRUM, en esta rama estaría el código sobre el cual se usaría para la implementación de las nuevas versiones y el manejo de una rama por cada Sprint que se esté desarrollando, se tomaría como base el código de la última versión certificada de la rama master.

Para el caso de los archivos properties, dentro de cada uno de los proyectos se tendrían 4 carpetas que contendrían los archivos .properties de cada ambiente dev, calidad y producción.
Para el caso de ejecución de varios Sprint en paralelo que modifiquen algún componente en común se debe realizar un merge manual antes de que se envíe a pruebas.

- [Ref: Versioning](https://github.com/UniandesDSIT/coding-guidelines/blob/master/versioning/VERSIONING.md)

<img src="https://github.com/UniandesDSIT/coding-guidelines/blob/master/assets/img/hotfix_branches.PNG?raw=true" width="750" height="400" />

[ **[Volver al Menú Principal](MAIN.md)** ]

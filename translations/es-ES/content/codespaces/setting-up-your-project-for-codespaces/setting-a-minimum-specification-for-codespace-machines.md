---
title: Configurar una especificación mínima para las máquinas de los codespaces
shortTitle: Configurar una especificación de máquina mínima
intro: 'Puedes evitar que los tipos de máquina con recursos insuficientes se utilicen en los {% data variables.product.prodname_codespaces %} de tu repositorio.'
permissions: People with write permissions to a repository can create or edit the codespace configuration.
versions:
  fpt: '*'
  ghec: '*'
type: how_to
topics:
  - Codespaces
  - Set up
product: '{% data reusables.gated-features.codespaces %}'
---

## Resumen

Cuando crees un codespace para un repositorio, habitualmente se te ofrece elegir los tipos de máquina disponibles. Cada tipo de máquina tiene un nivel de recursos diferente. Para obtener más información, consulta la sección "[Cambiar el tipo de máquina de tu codespace](/codespaces/customizing-your-codespace/changing-the-machine-type-for-your-codespace#about-machine-types)".

Si tu proyecto necesita cierto nivel de potencia de cómputo, puedes configurar los {% data variables.product.prodname_github_codespaces %} para que solo los tipos de máquina que cumplan con estos requisitos se encuentren disponibles para que las personas los seleccionen. Puedes configurar esto en el archivo de `devcontainer.json`.

{% note %}

**Importante:** Puede que el acceso a algunos tipos de máquinas esté restringido a nivel organizacional. Habitualmente, esto se hace para prevenir que las personas elijan máquinas con recursos superiores, las cuales se cobran en tazas más altas. Si tu repositorio se ve afectado por la política de tipos de máquina a nivel organizacional, debes asegurarte de que no configures una especificación mínima que impida que las personas seleccionen los tipos de máquina disponibles que necesitan. Para obtener más información, consulta la sección "[Restringir el acceso a los tipos de máquina](/codespaces/managing-codespaces-for-your-organization/restricting-access-to-machine-types)".

{% endnote %}

## Configurar una especificación de máquina mínima

1. Los {% data variables.product.prodname_codespaces %} para tu repositorio se configuran en el archivo `devcontainer.json`. Si tu repositorio no contiene ya un archivo `devcontainer.json`, agrégalo ahora. Consulta "[Agregar un contenedor dev a tu proyecto](/free-pro-team@latest/codespaces/setting-up-your-project-for-codespaces/setting-up-your-project-for-codespaces)"
1. Edita el archivo `devcontainer.json` agregando una propiedad de `hostRequirements` tal como esta:

   ```json{:copy}
   "hostRequirements": {
      "cpus": 8,
      "memory": "8gb",
      "storage": "32gb" 
   }
   ```

   Puedes especificar todas o cualquiera de las opciones: `cpus`, `memory` y `storage`.

   Para verificar las especificaciones de los tipos de máquina de {% data variables.product.prodname_codespaces %} que actualmente están disponibles para tu repositorio, realiza el proceso de crear un codespace hasta que veas la elección de tipos de máquina. Para obtener más información, consulta la sección "[Crear un codespace](/codespaces/developing-in-codespaces/creating-a-codespace#creating-a-codespace)".

1. Guarda el archivo y confirma tus cambios a la rama requerida del repositorio.

   Ahora, cuando crees un codespace para esta rama del repositorio, solo podrás seleccionar tipos de máquina que coincidan o excedan los recursos que especificaste.

   ![Caja de diálogo que muestra una selección limitada de tipos de máquina](/assets/images/help/codespaces/machine-types-limited-choice.png)

## Leer más

- "[Introducción a los contenedores dev](/codespaces/setting-up-your-project-for-codespaces/configuring-codespaces-for-your-project)"

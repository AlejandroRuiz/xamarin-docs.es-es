---
title: "Compilación de XAML"
description: XAML se puede compilar de forma opcional directamente en lenguaje intermedio (IL) con el compilador XAML (XAMLC).
ms.topic: article
ms.prod: xamarin
ms.assetid: 9A2D10A6-5DFC-485F-A75A-2F7B98314025
ms.technology: xamarin-forms
author: charlespetzold
ms.author: chape
ms.date: 01/21/2016
ms.openlocfilehash: 3afb7608838a2c34f143d0563b50f03ad7f6ecf4
ms.sourcegitcommit: 6cd40d190abe38edd50fc74331be15324a845a28
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/27/2018
---
# <a name="xaml-compilation"></a>Compilación de XAML

_XAML se puede compilar opcionalmente directamente en lenguaje intermedio (IL) con el compilador XAML (XAMLC)._

XAMLC ofrece una serie de ventajas:

- Realiza la comprobación en tiempo de compilación de XAML, notificando al usuario de los errores.
- Reduce parte del tiempo de carga y creación de instancias para los elementos XAML.
- Facilita reducir el tamaño de archivo del ensamblado final al dejar de incluir archivos .xaml.

XAMLC está deshabilitado de forma predeterminada para garantizar la compatibilidad con versiones anteriores. Se puede habilitar en el nivel de clase y ensamblado agregando la `XamlCompilation` atributo.

En el ejemplo de código siguiente se muestra cómo habilitar XAMLC en el nivel de ensamblado:

```csharp
using Xamarin.Forms.Xaml;
...
[assembly: XamlCompilation (XamlCompilationOptions.Compile)]
namespace PhotoApp
{
  ...
}
```

En este ejemplo, comprobación en tiempo de compilación de todo el contenido XAML dentro de la `PhotoApp` se realizará espacio de nombres, con errores XAML que se va a notificar en tiempo de compilación en lugar de tiempo de ejecución.
El `assembly` anteponer a la `XamlCompilation` atributo especifica que el atributo se aplica a todo el ensamblado.

En el ejemplo de código siguiente se muestra cómo habilitar XAMLC en el nivel de clase:

```csharp
using Xamarin.Forms.Xaml;
...
[XamlCompilation (XamlCompilationOptions.Compile)]
public class HomePage : ContentPage
{
  ...
}
```

En este ejemplo, la comprobación del código XAML para el tiempo de compilación la `HomePage` clase se llevará a cabo y los errores se notifican como parte del proceso de compilación.

> [!NOTE]
> **Tenga en cuenta**: el `XamlCompilation` atributo y el `XamlCompilationOptions` enumeración residen en el `Xamarin.Forms.Xaml0` espacio de nombres, que se debe importar para usarlos.


## <a name="related-links"></a>Vínculos relacionados

- [XamlCompilation](https://developer.xamarin.com/api/type/Xamarin.Forms.Xaml.XamlCompilationAttribute/)
- [XamlCompilationOptions](https://developer.xamarin.com/api/type/Xamarin.Forms.Xaml.XamlCompilationOptions/)
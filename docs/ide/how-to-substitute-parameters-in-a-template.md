---
title: 在專案和項目範本中新增名稱參數
ms.date: 01/02/2018
ms.topic: how-to
helpviewer_keywords:
- template parameters
- template parameters, substituting
- Visual Studio templates, using parameters
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 3c8b6e0570567e8eb696fda61fe9db7bbd4a2f1b
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/23/2020
ms.locfileid: "85283940"
---
# <a name="how-to-substitute-parameters-in-a-template"></a>如何：替代範本中的參數

從範本建立檔案時，範本參數可讓您取代類別名稱和命名空間等識別碼。 您可以將範本參數新增至現有的範本，或使用範本參數建立您自己的範本。

以格式 $<參數>**$ 撰寫範本參數。 如需完整的範本參數清單，請參閱[範本參數](../ide/template-parameters.md)。

下節示範如何修改範本，以「安全的專案名稱」取代命名空間的名稱。

## <a name="example---namespace-name"></a>範例 - 命名空間名稱

1. 在範本的一或多個程式碼檔案中，插入參數。 例如：

    ```csharp
    namespace $safeprojectname$
    ```

1. 在範本的 *.vstemplate*檔案中，找出 `ProjectItem` 包含此檔案的元素。

1. 將 `ProjectItem` 項目的 `ReplaceParameters` 屬性設定為 `true`：

    ```xml
    <ProjectItem ReplaceParameters="true">Class1.cs</ProjectItem>
    ```

## <a name="see-also"></a>另請參閱

- [建立專案與項目範本](../ide/creating-project-and-item-templates.md)
- [範本參數](../ide/template-parameters.md)
- [Visual Studio 範本架構參考](../extensibility/visual-studio-template-schema-reference.md)
- [ProjectItem 項目 (Visual Studio 項目範本)](../extensibility/projectitem-element-visual-studio-item-templates.md)

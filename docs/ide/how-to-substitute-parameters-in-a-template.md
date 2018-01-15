---
title: "在 Visual Studio 的專案和項目範本中新增名稱參數 | Microsoft Docs"
ms.custom: 
ms.date: 01/02/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- template parameters
- template parameters, substituting
- Visual Studio templates, using parameters
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ecdd277a36cb1c074653edb2af7f1882e6d25ede
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2018
---
# <a name="how-to-substitute-parameters-in-a-template"></a>如何：替代範本中的參數

從範本建立檔案時，範本參數可讓您取代類別名稱和命名空間等識別碼。 您可以將範本參數新增至現有的範本，或使用範本參數建立您自己的範本。

以格式 $<參數>$ 撰寫範本參數。 如需完整的範本參數清單，請參閱[範本參數](../ide/template-parameters.md)。

下節示範如何修改範本，以「安全的專案名稱」取代命名空間的名稱。

## <a name="to-use-a-parameter-to-replace-the-namespace-name"></a>使用參數取代命名空間名稱

1. 在範本的一或多個程式碼檔案中，插入參數。 例如: 

    ```csharp
    namespace $safeprojectname$
    ```

1. 在範本的 .vstemplate 檔案中，找出包括此檔案的 `ProjectItem` 項目。

1. 將 `ProjectItem` 項目的 `ReplaceParameters` 屬性設定為 `true`：

    ```xml
    <ProjectItem ReplaceParameters="true">Class1.cs</ProjectItem>
    ```

## <a name="see-also"></a>另請參閱

[建立專案和項目範本](../ide/creating-project-and-item-templates.md)  
[範本參數](../ide/template-parameters.md)  
[Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)  
[ProjectItem 元素 (Visual Studio 項目範本)](../extensibility/projectitem-element-visual-studio-item-templates.md)
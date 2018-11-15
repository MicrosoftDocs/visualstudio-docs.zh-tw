---
title: 如何： 變更特定領域語言命名空間
ms.date: 10/31/2018
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, namespace
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 47e13e8399cba7762ff7443e4fc4cbf3a89375a6
ms.sourcegitcommit: 768d7877fe826737bafdac6c94c43ef70bf45076
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/02/2018
ms.locfileid: "50966826"
---
# <a name="how-to-change-the-namespace-of-a-domain-specific-language"></a>如何： 變更特定領域語言命名空間

您可以變更特定領域語言的命名空間。 進行中的變更**DSL explorer**、 Dsl 封裝專案屬性，以及組件資訊。

## <a name="to-change-the-namespace-of-a-domain-specific-language"></a>若要變更的特定領域語言命名空間

1. 在  **DSL Explorer**，選取**Dsl**節點。

2. 在 **屬性**視窗中，變更**命名空間**屬性。

3. 儲存方案，並轉換範本。

4. 在 **專案**功能表上，選擇**Dsl 屬性**。

   您的專案的屬性會出現。

5. 選取 [**應用程式**] 索引標籤。

6. 變更**預設命名空間**屬性設為新的命名空間名稱。

7. 如果您也想要變更的組件名稱，變更**組件名稱屬性。**

8. 如果您已變更的組件名稱，請開啟 DslPackage\Package.tt，並更新這一行：

   `string dslAssembly = "YourDSLassembly.Dsl.dll";`

9. 如果您已撰寫的自訂程式碼，確定變更程式碼檔案中的命名空間和類別的參考。

10. 重設 Visual Studio 實驗執行個體。

    1. 刪除**\Users\\**_{name}_**\AppData\Local\Microsoft\VisualStudio\\\*Exp**。

    2. 在 Windows 上**開始**功能表上，選擇**所有程式** > **Microsoft Visual Studio 2010 SDK** > **工具**  > **重設實驗執行個體**。

11. 在 **建置**功能表上，選擇**重建方案**。

## <a name="see-also"></a>另請參閱

[特定領域語言工具字彙](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
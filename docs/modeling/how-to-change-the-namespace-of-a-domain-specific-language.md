---
title: How to：變更特定領域語言的命名空間
ms.date: 10/31/2018
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, namespace
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b64a61c02f44db0ce70b758331d0d70f7bb8014d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72653774"
---
# <a name="how-to-change-the-namespace-of-a-domain-specific-language"></a>How to：變更特定領域語言的命名空間

您可以變更特定領域語言的命名空間。 在**Dsl Explorer**、dsl 封裝專案的屬性和元件資訊中進行變更。

## <a name="to-change-the-namespace-of-a-domain-specific-language"></a>變更特定領域語言的命名空間

1. 在 [ **Dsl Explorer**] 中，選取 [ **dsl** ] 節點。

2. 在 [**屬性**] 視窗中，變更 [**命名空間**] 屬性。

3. 儲存方案並轉換範本。

4. 在 [**專案**] 功能表上，選擇 [ **Dsl 屬性**]。

   專案的屬性隨即出現。

5. 選取 [**應用程式**] 索引標籤。

6. 將 [**預設命名空間**] 屬性變更為新的命名空間名稱。

7. 如果您也想要變更元件的名稱，請變更 [**元件名稱] 屬性。**

8. 如果您已變更元件名稱，請開啟 DslPackage\Package.tt，並更新這一行：

   `string dslAssembly = "YourDSLassembly.Dsl.dll";`

9. 如果您已撰寫任何自訂程式碼，請務必變更程式碼檔案中的命名空間和類別參考。

10. 重設 Visual Studio 實驗實例。

    1. 刪除 **\Users \\** _{您的名稱}_ **\AppData\Local\Microsoft\VisualStudio \\ \*Exp**。

    2. 在 Windows **開始** 功能表上，選擇 **所有程式**， > **Microsoft Visual Studio 2010 SDK**  > **工具**  > **重設實驗實例**。

11. 在 [**建立**] 功能表上，選擇 [**重建方案**]。

## <a name="see-also"></a>請參閱

[特定領域語言工具詞彙](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
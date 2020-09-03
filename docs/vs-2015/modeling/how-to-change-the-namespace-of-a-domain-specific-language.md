---
title: 如何：變更特定領域語言的命名空間 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, namespace
ms.assetid: f20c47e5-230d-4f0e-812f-5c6edb86866c
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8b61b248876f701e9d5286063f28b4f71d73e18b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671726"
---
# <a name="how-to-change-the-namespace-of-a-domain-specific-language"></a>如何：變更網域指定的語言命名空間
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以變更特定領域語言的命名空間。 您必須在 dsl **Explorer**、dsl 封裝專案的屬性，以及元件資訊中進行變更。

### <a name="to-change-the-namespace-of-a-domain-specific-language"></a>變更特定領域語言的命名空間

1. 在 [ **Dsl Explorer**] 中，按一下 [ **dsl** ] 節點。

2. 在 [ **屬性** ] 視窗中，變更 [ **命名空間** ] 屬性。

3. 儲存方案並轉換範本。

4. 在 [ **專案** ] 功能表上，按一下 [ **Dsl 屬性**]。

     專案的屬性隨即出現。

5. 按一下 [應用程式] **** 索引標籤。

6. 將 [ **預設命名空間** ] 屬性變更為新的命名空間名稱。

7. 如果您也要變更元件的名稱，請變更 [ **元件名稱] 屬性。**

8. 如果您已變更元件名稱，請開啟 DslPackage\Package.tt 並更新這一行：

     `string dslAssembly = "YourDSLassembly.Dsl.dll";`

9. 如果您已撰寫任何自訂程式碼，請務必變更程式碼檔案中的命名空間和類別參考。

10. 重設 Visual Studio 實驗實例。

    1. 刪除**\Users \\ ** _{您的名稱}_**\AppData\Local\Microsoft\VisualStudio \\ \* Exp**

    2. 在 Windows [ **開始** ] 功能表上，選擇 [ **所有程式**]、[ **Microsoft Visual Studio 2010 SDK**]、[ **工具**]、 **[重設實驗實例**]。

11. 在 [ **組建** ] 功能表上，選擇 [ **重建方案**]。

## <a name="see-also"></a>另請參閱
 [Domain-Specific Language Tools Glossary](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa) (特定領域語言工具字彙表)

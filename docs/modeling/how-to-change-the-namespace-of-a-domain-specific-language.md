---
title: 如何：變更網域指定的語言命名空間
ms.date: 11/04/2016
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
ms.openlocfilehash: 1963502f3940fd0d17c770f111e07de14207e687
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31948258"
---
# <a name="how-to-change-the-namespace-of-a-domain-specific-language"></a>如何：變更網域指定的語言命名空間
您可以變更特定領域語言命名的空間。 您必須進行的變更**DSL 總管**、 Dsl 封裝專案中，屬性和組件資訊。

### <a name="to-change-the-namespace-of-a-domain-specific-language"></a>若要變更的特定領域語言命名空間

1.  在**DSL 總管**，按一下  **Dsl**節點。

2.  在**屬性**視窗中，變更**命名空間**屬性。

3.  儲存方案，並轉換範本。

4.  在**專案**功能表上，按一下  **Dsl 屬性**。

     為您的專案屬性會出現。

5.  按一下 [應用程式]  索引標籤。

6.  變更**預設命名空間**屬性設為新的命名空間名稱。

7.  如果您也想要變更的組件名稱，變更**組件名稱屬性。**

8.  如果您已變更的組件名稱，開啟 DslPackage\Package.tt，並更新這一行：

     `string dslAssembly = "YourDSLassembly.Dsl.dll";`

9. 如果您已撰寫任何自訂程式碼，確定變更命名空間和類別的參考，程式碼檔案中。

10. 重設 Visual Studio 實驗執行個體。

    1.  刪除**\Users\\ ***{name}*** \AppData\Local\Microsoft\VisualStudio\\\*Exp**

    2.  在 Windows**啟動**功能表上，選擇**所有程式**， **Microsoft Visual Studio 2010 SDK**，**工具**，**重設實驗執行個體**。

11. 在**建置**功能表上，選擇**重建方案**。

## <a name="see-also"></a>另請參閱

- [特定領域語言工具詞彙](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
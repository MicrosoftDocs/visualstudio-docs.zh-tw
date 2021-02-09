---
title: 如何：開啟 Office 方案而不執行程式碼
description: 學習如何開啟包含 managed 程式碼延伸模組的檔或活頁簿，而不需要執行元件程式碼。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office solutions [Office development in Visual Studio], opening
- opening Office solutions
- bypassing assemblies
- solutions [Office development in Visual Studio], opening
- assemblies [Office development in Visual Studio], bypassing
- Office documents [Office development in Visual Studio, opening without running code
- documents [Office development in Visual Studio], opening without running code
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 99f1a01a745544e7e11e724db9c6eafacf0ca201
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99876585"
---
# <a name="how-to-open-office-solutions-without-running-code"></a>如何：開啟 Office 方案而不執行程式碼
  即使終端使用者的 Office 應用程式中的安全性設定設為 [高]，使用 managed 程式碼擴充功能建立的 Microsoft Office 方案仍會執行。 這是因為 .NET 元件碼安全性是由 Microsoft .NET Framework 管理，而不是由 Microsoft Office 管理。

 不過，有時候您可能會想要在不執行程式碼的情況下開啟檔。 例如，在檔開啟時執行的程式碼可能會改變內容，但您想要在程式碼變更之前，更新檔的外觀。 或者，您可能想要將檔中的某些資訊傳送給某人，而您不想讓程式碼執行，而且可能會改變內容。

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 有幾種方式可以開啟包含 managed 程式碼延伸模組的檔或活頁簿，而不需要執行元件程式碼。

## <a name="to-bypass-the-assembly-by-using-the-shift-key"></a>使用 Shift 鍵略過元件

- 從 [檔案] 功能表開啟 **檔** 和活頁簿，同時按住 **Shift** 鍵，以防止 Word 和 Excel 在檔開啟時引發初始化事件。

    > [!NOTE]
    > 如果您從 **開始使用** 工作窗格開啟檔或活頁簿，按住 **Shift** 並不會略過程式碼。 此外，按住 SHIFT 鍵並不會防止在檔開啟後引發事件。

     如果您想要在沒有執行程式碼的情況下進行變更並先變更檔，這個方法會很有用。

## <a name="to-bypass-an-assembly-by-renaming-or-removing-it"></a>重新命名或移除元件以略過元件

- 如果您在元件所在的電腦上有必要的許可權，您可以重新命名或移除元件，使檔或活頁簿找不到它。 這會導致每次開啟 Office 檔時引發錯誤。

     如果多人使用此方案，這個方法會防止解決方案針對所有人執行。 如果在程式碼或參考的伺服器中發現問題，而且您想要讓所有使用者都無法執行，這項功能就很有用。

## <a name="see-also"></a>另請參閱
- [保護 Office 方案](../vsto/securing-office-solutions.md)
- [部署 Office 方案](../vsto/deploying-an-office-solution.md)
- [設計和建立 Office 方案](../vsto/designing-and-creating-office-solutions.md)
- [Office 方案中的應用程式和部署資訊清單](../vsto/application-and-deployment-manifests-in-office-solutions.md)

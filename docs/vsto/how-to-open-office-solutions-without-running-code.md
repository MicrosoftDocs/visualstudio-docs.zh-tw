---
title: 如何：在不執行程式碼的情況下開啟 Office 方案
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d84515c2c3159b61b96f77555b23eef0df0ae961
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85543477"
---
# <a name="how-to-open-office-solutions-without-running-code"></a>如何：在不執行程式碼的情況下開啟 Office 方案
  即使終端使用者的 Office 應用程式中的安全性設定設為 [高]，使用 managed 程式碼擴充所建立的 Microsoft Office 方案仍會執行。 這是因為 .NET 組合語言程式碼安全性是由 Microsoft .NET Framework 所管理，而不是由 Microsoft Office。

 不過，有時候您可能會想要開啟檔，而不需要執行程式碼。 例如，當檔開啟時執行的程式碼可能會改變內容，但是您想要更新檔在程式碼變更之前的外觀。 或者，您可能想要將含有特定資訊的檔傳送給其他人，而且您不想要讓程式碼執行，而且可能會更改內容。

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 有幾種方式可以開啟包含 managed 程式碼擴充的檔或活頁簿，而不需要執行元件程式碼。

## <a name="to-bypass-the-assembly-by-using-the-shift-key"></a>若要使用 Shift 鍵略過元件

- 在按住**Shift**鍵時，從 [檔案] 功能表開啟 [**檔**和活頁簿]，以防止 Word 和 Excel 在檔開啟時引發初始化事件。

    > [!NOTE]
    > 如果您從 [**消費者入門**工作窗格] 開啟檔或活頁簿，按住**Shift**並不會略過程式碼。 此外，按住 SHIFT 並不會防止在開啟檔後引發事件。

     如果您想要開啟檔進行變更，而不執行程式碼，並先改變檔，這個方法就很有用。

## <a name="to-bypass-an-assembly-by-renaming-or-removing-it"></a>藉由重新命名或移除元件來略過

- 如果您在元件所在的電腦上有必要的許可權，您可以重新命名或移除該元件，讓檔或活頁簿找不到它。 這會導致每次開啟 Office 檔時引發錯誤。

     如果有多人使用此解決方案，這個方法會讓解決方案不會針對所有使用者執行。 如果在程式碼或參照的伺服器中發現問題，而您想要停止所有使用者執行它，這會很有用。

## <a name="see-also"></a>另請參閱
- [保護 Office 方案](../vsto/securing-office-solutions.md)
- [部署 Office 方案](../vsto/deploying-an-office-solution.md)
- [設計和建立 Office 方案](../vsto/designing-and-creating-office-solutions.md)
- [Office 方案中的應用程式和部署資訊清單](../vsto/application-and-deployment-manifests-in-office-solutions.md)

---
title: Office 方案的共同開發
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], collaborative development
- Office development in Visual Studio, collaboration
- source control [Office development in Visual Studio]
- collaborative development [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 76c26a110d88d3dee8bf7540647ea0bfde4e7c4f
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56635055"
---
# <a name="collaborative-development-of-office-solutions"></a>Office 方案的共同開發
  多位開發人員可以使用 Office 專案中相同的方式，他們在其他 Visual Studio 專案上共同作業。 Visual Studio 正確找出每一部做為 Microsoft Office 安裝，即使 Office 會安裝在不同的位置。 不過，有一些重要的考量来留意。

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="debug-properties-are-not-shared"></a>偵錯不會共用屬性
 偵錯屬性不是在原始檔控制中由多位使用者共用。 Visual Basic 和 VisualC#專案的偵錯屬性儲存在特定使用者的檔案 (*ProjectName*.vbproj.user 或*ProjectName*.csproj.user)，而這個檔案不在原始檔控制. 如果有多人同時進行偵錯，每個人都必須手動輸入偵錯屬性。

 如果專案位於原始檔控制中而不是網路共用上，必須採取一些額外的步驟讓共同作業的開發人員開啟方案，並測試組件。

## <a name="source-control-requires-checking-out-all-files"></a>原始檔控制需要簽出的所有檔案
 如果您使用原始檔控制專案時，您應該查看的所有檔案中的程式碼檔案下**方案總管**(例如*ThisDocument*， *ThisWorkbook*，或*ThisAddIn*程式碼檔案) 每次您變更程式碼檔案，即使是預設為隱藏的檔案。 如果您查看只有最上層程式碼檔案時，您的變更可能會遺失。

 您進行變更之後，請檢查所有檔案備份中。 如需有關專案中的隱藏程式碼檔案的詳細資訊，請參閱[Visual Studio 環境中的 Office 專案](../vsto/office-projects-in-the-visual-studio-environment.md)。

## <a name="security-for-informal-collaboration-on-a-network"></a>在網路上的非正式共同作業安全性
 網路位置中的所有文件層級解決方案 (例如\\ \\ *Servername*\\*Sharename*)，完整限定的位置必須新增至您正在使用的 Microsoft Office 應用程式中受信任的資料夾清單。 選取的選項包含子目錄的主要資料夾下方，或特別新增偵錯，然後建置到受信任的資料夾清單的資料夾。 如需如何執行這項操作的詳細資訊，請參閱[授與信任給文件](../vsto/granting-trust-to-documents.md)。

 在建置階段自動產生的暫時憑證不受保護的密碼。 憑證中包含開發人員的登入名稱和其他個人資訊。 如果您部署自訂的暫時憑證所簽署時，其他人可以存取這項資訊。

## <a name="see-also"></a>另請參閱
- [保護 Office 方案](../vsto/securing-office-solutions.md)
- [設計和建立 Office 方案](../vsto/designing-and-creating-office-solutions.md)
- [建置 Office 方案](../vsto/building-office-solutions.md)

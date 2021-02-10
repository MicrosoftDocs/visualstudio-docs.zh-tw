---
title: Office 方案的共同開發
description: 瞭解多個開發人員如何以與其他 Visual Studio 專案共同作業相同的方式，來處理 Office 專案。
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 028530014afdc78ab6c9c0483c3d443195383793
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99942304"
---
# <a name="collaborative-development-of-office-solutions"></a>Office 方案的共同開發
  多個開發人員可以使用與其他 Visual Studio 專案共同作業的相同方式來處理 Office 專案。 Visual Studio 在每部電腦上正確地找到 Microsoft Office 安裝，即使 Office 安裝在不同的位置。 不過，有一些重要的考慮要留意。

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="debug-properties-are-not-shared"></a>不共用 Debug 屬性
 偵錯屬性不是在原始檔控制中由多位使用者共用。 Visual Basic 和 Visual c # 專案會將偵錯工具屬性儲存在使用者專屬的檔案中 *， (vbproj*. 使用者或 *專案名稱*。使用者) ，而這個檔案不在原始檔控制之下。 如果有多人同時進行偵錯，每個人都必須手動輸入偵錯屬性。

 如果專案是存放在網路共用上，而不是在原始檔控制中，則必須採取一些額外的步驟，讓共同作業的開發人員可以開啟方案並測試元件。

## <a name="source-control-requires-checking-out-all-files"></a>原始檔控制需要簽出所有檔案
 如果您在專案中使用原始檔控制，您應該 (**方案總管** 在每次變更程式碼檔案時，簽出程式碼檔下的所有檔案（例如 *ThisDocument*、 *ThisWorkbook* 或 *ThisAddIn* 程式碼檔案）) ，甚至是預設隱藏的檔案。 如果您只簽出最上層程式碼檔案，您的變更可能會遺失。

 進行變更之後，請將所有檔案存回。 如需有關專案中隱藏程式碼檔案的詳細資訊，請參閱 [Visual Studio 環境中的 Office 專案](../vsto/office-projects-in-the-visual-studio-environment.md)。

## <a name="security-for-informal-collaboration-on-a-network"></a>網路上非正式協同作業的安全性
 針對網路位置中的所有檔層級解決方案 (例如 \\ \\ *Servername* \\ *共用*) ，必須將完整位置新增至您正在使用之 Microsoft Office 應用程式中的信任資料夾清單。 選取 [主要資料夾] 底下的子目錄，或特別將 [debug] 和 [組建資料夾] 加入至 [信任的資料夾] 清單中的選項。 如需如何進行的詳細資訊，請參閱 [授與信任給檔](../vsto/granting-trust-to-documents.md)。

 在組建階段自動產生的暫時性憑證不受密碼保護。 憑證包含開發人員的登入名稱和其他個人資訊。 如果您部署由暫時性憑證簽署的自訂，其他人可能可以存取此資訊。

## <a name="see-also"></a>另請參閱
- [保護 Office 方案](../vsto/securing-office-solutions.md)
- [設計和建立 Office 方案](../vsto/designing-and-creating-office-solutions.md)
- [建立 Office 方案](../vsto/building-office-solutions.md)

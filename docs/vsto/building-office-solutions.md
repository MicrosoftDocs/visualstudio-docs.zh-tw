---
title: 建立 Office 方案
description: 瞭解在 Visual Studio 中建立和調試 Office 專案，以及建立和偵錯工具的其他專案類型的差異，例如 Windows Forms。
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- debugging [Office development in Visual Studio]
- debugging Office applications in Visual Studio
- solutions [Office development in Visual Studio], debugging
- Office applications [Office development in Visual Studio], debugging
- application development [Office development in Visual Studio], building
- Office applications [Office development in Visual Studio], building
- projects [Office development in Visual Studio], debugging
- Office solutions [Office development in Visual Studio], building
- solutions [Office development in Visual Studio], building
- Office projects [Office development in Visual Studio], debugging
- projects [Office development in Visual Studio], building
- builds [Office development in Visual Studio]
- Office projects [Office development in Visual Studio], building
- application development [Office development in Visual Studio], debugging
- Office solutions [Office development in Visual Studio], debugging
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 31cb28ad2c332d0afea9bef8cbe1c979b58536e6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99896720"
---
# <a name="build-office-solutions"></a>建立 Office 方案
  一般而言，建置和偵錯 Office 專案，和在 Visual Studio 中建置和偵錯其他類型的專案是相同的，例如 Windows Forms。 本節主題會說明兩者之間的差異。 如需如何建立應用程式的一般資訊，請參閱 [Visual Studio 中的編譯和建立](../ide/compiling-and-building-in-visual-studio.md)。

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="project-output-for-office-projects"></a>Office 專案的專案輸出
 Office 專案的輸出位置是 *projectname*\bin\release 或 *projectname*\bin\debug。 無法建立到部署目錄。

### <a name="document-level-projects"></a>檔層級專案
 當您建置文件層級專案時，專案輸出會包含下列項目：

- 一份專案文件的複本。

- 其 [複製到本機]  屬性設定為 **true** 的專案組件和所有參考組件。

- 應用程式資訊清單，其副檔名為 *.manifest*。 如需詳細資訊，請參閱 [Office 方案的應用程式資訊清單](../vsto/application-manifests-for-office-solutions.md)。

- 具有副檔名 *vsto* 的部署資訊清單。 如需詳細資訊，請參閱 [Office 方案的部署資訊清單](../vsto/deployment-manifests-for-office-solutions.md)。

- 程式資料庫 (*PDB*) 檔。

> [!NOTE]
> 文件層級解決方案如果建立在遠端位置而不是本機電腦，請在應用程式信任中心的 [信任位置] 清單中加入完整的路徑。 如需詳細資訊，請參閱將信任授與 [安全 Office 方案](../vsto/securing-office-solutions.md)中的檔一節。

### <a name="application-level-projects"></a>應用層級專案
 當您建立 VSTO 增益集專案時，專案輸出中會包含下列專案：

- 其 [複製到本機]  屬性設定為 **true** 的專案組件和所有參考組件。

- 應用程式資訊清單，其副檔名為 *.manifest*。 如需詳細資訊，請參閱 [Office 方案的應用程式資訊清單](../vsto/application-manifests-for-office-solutions.md)。

- 具有副檔名 *vsto* 的部署資訊清單。 如需詳細資訊，請參閱 [Office 方案的部署資訊清單](../vsto/deployment-manifests-for-office-solutions.md)。

- 專案元件的程式資料庫 (*PDB*) 檔。

  VSTO 增益集專案的建置程序也會在需要載入 VSTO 增益集的開發電腦上建立一組登錄項目。 如需詳細資訊，請參閱 [VSTO 增益集的登錄專案](../vsto/registry-entries-for-vsto-add-ins.md)。

  如果您建置了包含表單區域的 Outlook VSTO 增益集專案，建置程序會在登錄中加入以下額外的資訊：

- 與一個或多個表單區域關聯之每個訊息類別的索引鍵。

- 每個表單區域的項目，以及代表 Outlook VSTO 增益集名稱的關聯值。

  Outlook 需要這項資訊載入表單區域。

## <a name="referenced-assemblies"></a>參考的組件
 您可以參考您「建置 Office 解決方案」專案的組件 (包括類別庫專案)。 每個參考的組件都有稱為 [複製到本機] 的屬性。 [複製到本機] 指出組件是否要複製到輸出目錄。 依預設，它會設定為 **true**。 每個將 [複製到本機]  設為 **true** 的參考組件都會複製到輸出目錄。

## <a name="security-during-the-build-process"></a>組建流程期間的安全性
 Visual Studio 會自動設定開發電腦的安全性設定，在建置程序期間將信任授與解決方案。 這讓解決方案在被偵錯時依然執行。

 Office 專案使用憑證來驗證發行者。 Visual Studio 會自動建立暫時憑證以識別 Office 解決方案，並設定開發電腦信任暫時的憑證。

 如需詳細資訊，請參閱 [安全的 Office 方案](../vsto/securing-office-solutions.md)。

### <a name="network-projects"></a>網路專案
 如果組件或文件位置位在網路共用上，則本機 (使用者層級) 的安全性原則更新將不足以允許解決方案執行。 系統管理員必須先將電腦層級的完全信任授與網路共用上的組件和文件，解決方案才會執行。 如需如何設定安全性原則的詳細資訊，請參閱 [安全的 Office 方案](../vsto/securing-office-solutions.md)。

 針對文件層級專案，您也必須在 Office 的信任資料夾清單中加入文件的完整路徑位置。 如需詳細資訊，請參閱 [授與信任給檔](../vsto/granting-trust-to-documents.md)。

## <a name="change-the-platform-target"></a>變更平臺目標
 Office 專案的平台目標預設是 **任何 CPU**。 通常不應該變更這項設定。 使用平台目標設定為 **任何 CPU** 所建置的 Office 解決方案，可在 32 位元和 64 位元版本的 Microsoft [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] 或 [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]中執行。

 只有建立只能在 64 位元版本的 Microsoft [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] 或 [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]中執行的解決方案時，才將平台目標設定為 x64，而這種解決方案需要原生的 64 位元應用程式開發介面。 如需變更平臺目標設定的詳細資訊，請參閱 [如何：將專案設定成以平臺為目標](../ide/how-to-configure-projects-to-target-platforms.md)。

 如果平台目標設定為 x64，解決方案就不能在 32 位元版本的 Windows 或 Office 中執行。 X64 平台目標需要解決方案在 64 位元處理序中執行。

## <a name="use-the-clean-command"></a>使用 Clean 命令
 若要從開發電腦中移除已建置的專案檔案，您可以使用 **之 [建置]****功能表的 [清除]**[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]命令。 [清除]  命令會刪除建置輸出位置的所有檔案。 至於應用程式層級專案，[清除]  命令也會移除建置程序所建立的登錄項目。

## <a name="related-topics"></a>相關主題

|標題|描述|
|-----------|-----------------|
|[Debug Office 專案](../vsto/debugging-office-projects.md)|列出偵錯 Office 專案的相關問題。|
|[逐步解說：建立 Excel 的第一個檔層級自訂](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)|示範如何建立 Excel 的基本文件層級自訂。|
|[如何：重新啟用已停用的 VSTO 增益集](../vsto/how-to-re-enable-a-vsto-add-in-that-has-been-disabled.md)|說明如何重新啟用已硬式或已停用的 VSTO 增益集。|
|[設計和建立 Office 方案](../vsto/designing-and-creating-office-solutions.md)|提供建立 Office 解決方案以及解決方案之組件角色相關資訊的連結。|
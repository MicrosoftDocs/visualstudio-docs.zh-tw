---
title: 檔層級自訂的架構
description: 瞭解檔層級自訂的各個層面，包括自訂群組件，以及自訂如何與 Microsoft Office 的應用程式搭配運作。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- VSTOLoader.dll
- formats [Office development in Visual Studio]
- file formats [Office development in Visual Studio]
- vstoee.dll
- managed code extensions [Office development in Visual Studio], definition
- document-level customizations [Office development in Visual Studio]
- AddInLoader.dll
- architecture [Office development in Visual Studio], document-level customizations
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: a101fa597764538c0a1c09e7b4e5de2c81606346
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948722"
---
# <a name="architecture-of-document-level-customizations"></a>檔層級自訂的架構
  [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] 包含的專案可以建立 Microsoft Office Word 和 Microsoft Office Excel 的文件層級自訂。 本主題描述文件層級自訂的下列各方面：

- [瞭解自訂](#UnderstandingCustomizations)

- [自訂的元件](#Components)

- [自訂如何與 Microsoft Office 的應用程式搭配運作](#HowCustomizationsWork)

  [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

  如需有關建立檔層級自訂的一般資訊，請參閱 [Office 方案開發總覽 &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)、 [開始撰寫 Word 的檔層級自訂](../vsto/getting-started-programming-document-level-customizations-for-word.md)，以及 [開始設計 Excel 的檔層級自訂](../vsto/getting-started-programming-document-level-customizations-for-excel.md)。

## <a name="understand-customizations"></a><a name="UnderstandingCustomizations"></a> 瞭解自訂
 當您使用 Visual Studio 中的 Office Developer Tools 建置文件層級自訂時，會建立與特定文件相關聯的 Managed 程式碼組件。 文件或活頁簿中若是有連結的組件就稱為具有 Managed 程式碼擴充。 如需詳細資訊，請參閱 [設計和建立 Office 方案](../vsto/designing-and-creating-office-solutions.md)。

 當使用者開啟文件時，Microsoft Office 應用程式會載入組件。 載入組件之後，自訂就能回應開啟文件時的事件。 自訂還可以呼叫物件模型，以在開啟文件時自動化及擴充應用程式，而且它可以使用 [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)]中的任何類別。

 組件會透過應用程式的主要 Interop 組件與應用程式的 COM 元件進行通訊。 如需詳細資訊，請參閱 [office 主要 interop 元件](../vsto/office-primary-interop-assemblies.md) 和 [office 方案開發總覽 &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)。

 如果使用者同時開啟多個文件層級自訂，每個組件會在不同的應用程式定義域中載入。 這表示如果某個方案運作失常，並不會導致其他方案失敗。 文件層級自訂設計成搭配單一應用程式定義域中的單一文件使用， 而不是設計成跨文件進行通訊。 如需應用程式域的詳細資訊，請參閱 [應用程式域](/dotnet/framework/app-domains/application-domains)。

> [!NOTE]
> 使用 Visual Studio 中的 Office Developer Tools 所建立的文件層級自訂，設計成只能在使用者啟動應用程式時使用。 如果是以程式設計的方式啟動應用程式 (例如，使用 Automation)，則該自訂可能無法如預期般運作。

### <a name="design-time-and-run-time-experiences"></a>設計階段和執行時間體驗
 了解設計方案和執行方案的體驗，有助於了解文件層級自訂的架構。

#### <a name="design-time"></a>設計階段
 設計階段體驗包含下列步驟：

1. 開發人員在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]中建立文件層級專案。 該專案會包含文件，以及在文件背後執行的組件。 檔可能已存在 (由設計工具) 所建立，或者可以與專案一起建立新的檔。

2. 設計人員 (建立專案的開發人員或其他人) 建立呈現給使用者的文件最終外觀與風格。

#### <a name="runtime"></a>執行階段
 執行階段體驗包含下列步驟：

1. 使用者開啟具有 Managed 程式碼擴充的文件或活頁簿。

2. 文件或活頁簿載入已編譯的組件。

3. 組件回應使用者處理文件或活頁簿時的事件。

#### <a name="developer-and-end-user-perspective-compared"></a>開發人員和終端使用者觀點比較
 由於開發人員主要是在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]中工作，而使用者是在 Word 或 Excel 中工作，因此可分為兩方面來了解文件層級自訂。

|開發人員觀點|使用者觀點|
|-----------------------------|----------------------------|
|開發人員可以使用 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]撰寫 Word 和 Excel 能夠存取的程式碼。<br /><br /> 雖然看起來好像是開發人員要建立執行 Word 或 Excel 的可執行檔，但實際上是完全相反的程序。 文件會與一個組件相關聯，並且含有指向該組件的指標。 當文件開啟時，Word 或 Excel 會尋找這個組件並執行程式碼，以回應所有已處理的事件。|使用方案的任何人只要開啟文件或活頁簿 (或者從範本建立新文件)，就像開啟其他任何 Microsoft Office 檔案一樣。<br /><br /> 該組件會提供文件或活頁簿中的自訂，例如以目前的資料自動填入，或顯示要求資訊的對話方塊。|

### <a name="supported-document-formats-for-document-level-customizations"></a>檔層級自訂支援的檔案格式
 當您建立自訂專案時，您可以選擇要在專案中使用的文件格式。 如需詳細資訊，請參閱 [如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。

 下表列出您可以在 Excel 和 Word 的文件層級自訂中使用的文件格式。

|Excel|Word|
|-----------|----------|
|Excel 活頁簿 (*.xlsx*) <br /><br /> Excel 啟用巨集活頁簿 (*. xlsm*) <br /><br /> Excel 二進位活頁簿 (*. .xlsb*) <br /><br /> Excel 97-2003 活頁簿 (*.xls*) <br /><br /> Excel 範本 (*. xltx*) <br /><br /> 已啟用 Excel 宏的範本 (*. xltm*) <br /><br /> Excel 97-2003 範本 (*.xlt*) |Word 檔 (*.docx*) <br /><br /> Word 啟用巨集檔 (*docm*) <br /><br /> Word 97-2003 檔 (*.doc*) <br /><br /> *Dotx) 的* Word 範本 (<br /><br /> Word 啟用巨集範本 (*normal.dotm*) <br /><br /> Word 97-2003 範本 (*的. 點*) |

 您只能以支援的格式為文件設計 Managed 程式碼擴充。 否則，當文件在應用程式中開啟時，可能無法引發特定事件。 例如， <xref:Microsoft.Office.Tools.Excel.Workbook.Open> 當您使用 managed 程式碼延伸模組搭配以 EXCEL XML 試算表格式儲存的活頁簿，或在網頁 (.htm 時，不會引發事件 *。**.html*) 格式。

### <a name="support-for-word-documents-that-have-xml-file-name-extensions"></a>支援具有 .xml 副檔名的 Word 檔
 文件層級專案範本不允許您建立以下列檔案格式為基礎的專案：

- Word XML 檔 (*\* XML*) 。

- Word 2003 XML 檔 (*\* xml*) 。

  如果您希望使用者使用這些檔案格式的自訂，請將自訂建置和部署為使用上表指定的其中一個支援的檔案格式。 安裝自訂之後，使用者可以將檔儲存為 Word XML 檔 (*\* Xml*) 格式或 Word 2003 xml 檔 (*\* xml*) 格式，自訂將繼續如預期般運作。

## <a name="components-of-customizations"></a><a name="Components"></a> 自訂群組件
 自訂的主要元件是文件和組件。 除了這些元件之外，還有其他數個組件在 Microsoft Office 應用程式探索和載入自訂的方式中扮演重要角色。

### <a name="deployment-manifest-and-application-manifest"></a>部署資訊清單和應用程式資訊清單
 自訂使用部署資訊清單和應用程式資訊清單，來識別及載入最新版的自訂組件。 部署資訊清單會指向目前的應用程式資訊清單。 而應用程式資訊清單會指向自訂組件，並指定要在組件中執行的一或多個進入點類別。 如需詳細資訊，請參閱 [Office 方案中的應用程式和部署資訊清單](../vsto/application-and-deployment-manifests-in-office-solutions.md)。

### <a name="visual-studio-tools-for-office-runtime"></a>Visual Studio Tools for Office Runtime
 若要執行使用 Visual Studio 中的 Office developer tools 所建立的檔層級自訂，終端使用者電腦必須已 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 安裝。 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 包含可載入自訂組件的 Unmanaged 元件，以及一組 Managed 組件。 這些 Managed 組件提供自訂程式碼用來自動化及擴充主應用程式的物件模型。

 如需詳細資訊，請參閱 [Visual Studio tools For Office runtime 總覽](../vsto/visual-studio-tools-for-office-runtime-overview.md)。

## <a name="how-customizations-work-with-microsoft-office-applications"></a><a name="HowCustomizationsWork"></a> 自訂如何與 Microsoft Office 的應用程式搭配運作
 當使用者開啟屬於 Microsoft Office 自訂一部分的文件時，應用程式會使用連結至該文件的部署資訊清單，來尋找及載入最新版的自訂組件。 部署資訊清單的位置會儲存在名為 **AssemblyLocation** 的自訂文件屬性中。 建置方案時，識別這個位置的字串會插入至這個屬性。

 部署資訊清單會指向應用程式資訊清單，而應用程式資訊清單則會指向最新的組件。 如需詳細資訊，請參閱 [Office 方案中的應用程式和部署資訊清單](../vsto/application-and-deployment-manifests-in-office-solutions.md)。

 下圖顯示文件層級自訂的基本架構。

 ![2007 Office 自訂架構](../vsto/media/office07-custom.png "2007 Office 自訂架構")

> [!NOTE]
> 在以 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]為目標的 Office 方案中，方案會使用內嵌於方案組件中的主要 Interop 組件 (PIA) 類型資訊來呼叫主應用程式的物件模型，而不是直接呼叫 PIA。 如需詳細資訊，請參閱 [設計和建立 Office 方案](../vsto/designing-and-creating-office-solutions.md)。

### <a name="loading-process"></a>載入處理序
 當使用者開啟屬於 Microsoft Office 方案一部分的文件時，會執行下列步驟。

1. Microsoft Office 應用程式會檢查自訂文件屬性，以查看文件是否有相關聯的 Managed 程式碼擴充。 如需詳細資訊，請參閱 [自訂文件屬性總覽](../vsto/custom-document-properties-overview.md)。

2. 如果有 managed 程式碼延伸模組，應用程式會載入 *VSTOEE.dll*，以載入 *VSTOLoader.dll*。 這些是非受控 Dll，這些 Dll 是適用于 Visual Studio 2010 Tools for Office runtime 的載入器元件。 如需詳細資訊，請參閱 [Visual Studio Tools for Office 執行時間總覽](../vsto/visual-studio-tools-for-office-runtime-overview.md)。

3. *VSTOLoader.dll* 載入 [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] ，並啟動的 managed 部分 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 。

4. 如果從本機電腦以外的位置開啟文件， [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 會確認文件的位置是否在該特定 Office 應用程式之 [信任中心設定]  的 [信任位置]  清單中。 如果文件位置不是在信任的位置中，則不會信任自訂，且載入程序會在這裡停止。

5. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 會安裝尚未安裝的方案、下載最新的應用程式和部署資訊清單，並執行一系列的安全性檢查。 如需詳細資訊，請參閱 [安全的 Office 方案](../vsto/securing-office-solutions.md)。

6. 如果自訂受信任而得以執行，則 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 會使用部署資訊清單和應用程式資訊清單來檢查組件更新。 如果有新版的組件可用，執行階段就會將新版的組件下載至用戶端電腦上的 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 快取。 如需詳細資訊，請參閱 [部署 Office 方案](../vsto/deploying-an-office-solution.md)。

7. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 會建立新的應用程式定義域，以便載入自訂組件。

8. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 會將自訂組件載入至此應用程式定義域中。

9. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 呼叫自訂組件中的 **Startup** 事件處理常式。 如需詳細資訊，請參閱 [Office 專案中的事件](../vsto/events-in-office-projects.md)。

## <a name="see-also"></a>另請參閱
- [Visual Studio 中的 Office 方案架構](../vsto/architecture-of-office-solutions-in-visual-studio.md)
- [VSTO 增益集的架構](../vsto/architecture-of-vsto-add-ins.md)
- [Visual Studio Tools for Office 執行時間總覽](../vsto/visual-studio-tools-for-office-runtime-overview.md)
- [保護 Office 方案](../vsto/securing-office-solutions.md)
- [設計和建立 Office 方案](../vsto/designing-and-creating-office-solutions.md)
- [自訂文件屬性總覽](../vsto/custom-document-properties-overview.md)
- [檔層級自訂中的快取資料](../vsto/cached-data-in-document-level-customizations.md)

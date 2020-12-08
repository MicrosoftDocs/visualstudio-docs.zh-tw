---
title: VSTO 增益集的架構
description: 在 Visual Studio 中建立的 VSTO 增益集具有可強調穩定性和安全性的架構功能，並可讓這些增益集與 Microsoft Office 緊密搭配運作。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- VSTOLoader.dll
- architecture [Office development in Visual Studio], application-level add-ins
- vstoee.dll
- application-level add-ins [Office development in Visual Studio], architecture
- add-ins [Office development in Visual Studio], architecture
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 451ae0bd466403819a5b4e53d76070876d762c38
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/08/2020
ms.locfileid: "96848348"
---
# <a name="architecture-of-vsto-add-ins"></a>VSTO 增益集的架構
  使用 Visual Studio 中 Office Developer Tools 建立的 VSTO 增益集具有同時強調穩定性和安全性的架構功能，這些功能可讓其與 Microsoft Office 密切合作。 本主題描述 VSTO 增益集的下列層面：

- [瞭解 VSTO 增益集](#UnderstandingAddIns)

- [VSTO 增益集的元件](#AddinComponents)

- [VSTO 增益集搭配 Microsoft Office 應用程式的運作方式](#HowAddinsWork)

  [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

  如需有關建立 VSTO 增益集的一般資訊，請參閱 [Office 方案開發總覽 &#40;vsto&#41;](../vsto/office-solutions-development-overview-vsto.md) 和 [開始程式設計 vsto 增益集](../vsto/getting-started-programming-vsto-add-ins.md)。

## <a name="understand-vsto-add-ins"></a><a name="UnderstandingAddIns"></a> 瞭解 VSTO 增益集
 當您使用 Visual Studio 中的 Office developer tools 建立 VSTO 增益集時，會建立由 Microsoft Office 應用程式載入的 managed 程式碼元件。 載入此組件之後，VSTO 該增益集就能回應應用程式所引發的事件 (例如，當使用者按一下功能表項目時)。 VSTO 增益集還可呼叫物件模型以自動化並擴充應用程式，而且它可以使用 [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)]中的任何類別。

 組件會透過應用程式的主要 Interop 組件與應用程式的 COM 元件進行通訊。 如需詳細資訊，請參閱 [office 主要 interop 元件](../vsto/office-primary-interop-assemblies.md) 和 [office 方案開發總覽 &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)。

 如果針對應用程式安裝多個 VSTO 增益集，則每一個 VSTO 增益集會在不同的應用程式定義域中載入。 這表示如果某個 VSTO 增益集運作失常，並不會導致其他 VSTO 增益集失敗。 此外，這樣有助於確保應用程式關閉後，所有 VSTO 增益集組件都會從記憶體中卸載。 如需應用程式域的詳細資訊，請參閱 [應用程式域](/dotnet/framework/app-domains/application-domains)。

> [!NOTE]
> 您使用 Visual Studio 中的 Office Developer Tools 建立的 VSTO 增益集，是設計為只在使用者啟動 Microsoft Office 主應用程式時使用。 如果是以程式設計的方式啟動應用程式 (例如，使用 Automation)，則該 VSTO 增益集可能無法如預期般運作。

## <a name="components-of-vsto-add-ins"></a><a name="AddinComponents"></a> VSTO 增益集的元件
 雖然 VSTO 增益集組件為主要元件，但還有其他數個元件在 Microsoft Office 應用程式探索和載入 VSTO 增益集的方式中扮演重要角色。

### <a name="registry-entries"></a>登錄項目
 Microsoft Office 應用程式會藉由尋找一組登錄項目來探索 VSTO 增益集。 如需 VSTO 增益集所使用之登錄專案的完整清單，請參閱 [Vsto 增益集的登錄專案](../vsto/registry-entries-for-vsto-add-ins.md)。

 當您建置方案時，Visual Studio 會在開發電腦上建立所有必要的登錄項目，以便您偵錯和執行 VSTO 增益集。 如需詳細資訊，請參閱 [建立 Office 方案](../vsto/building-office-solutions.md)。

 如果您使用 ClickOnce 部署方案，則發佈程式所產生的安裝程式會自動在終端使用者電腦上建立登錄機碼。 如需詳細資訊，請參閱 [使用 ClickOnce 部署 Office 方案](../vsto/deploying-an-office-solution-by-using-clickonce.md)。

### <a name="deployment-manifest-and-application-manifest"></a>部署資訊清單和應用程式資訊清單
 VSTO 增益集會使用部署資訊清單和應用程式資訊清單來識別及載入最新版的 VSTO 增益集組件。 部署資訊清單會指向目前的應用程式資訊清單。 而應用程式資訊清單會指向 VSTO 增益集組件，並指定要在組件中執行的進入點類別。 如需詳細資訊，請參閱 [Office 方案中的應用程式和部署資訊清單](../vsto/application-and-deployment-manifests-in-office-solutions.md)。

### <a name="visual-studio-tools-for-office-runtime"></a>Visual Studio Tools for Office Runtime
 若要執行使用 Visual Studio 中的 Office developer tools 所建立的 VSTO 增益集，終端使用者電腦必須已 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 安裝。 此執行階段包含 Unmanaged 元件和一組 Managed 組件。 Unmanaged 元件會載入 VSTO 增益集組件。 Managed 組件則會提供 VSTO 增益集程式碼用來自動化及擴充主應用程式的物件模型。

 如需詳細資訊，請參閱 [Visual Studio Tools for Office 執行時間總覽](../vsto/visual-studio-tools-for-office-runtime-overview.md)。

## <a name="how-vsto-add-ins-work-with-microsoft-office-applications"></a><a name="HowAddinsWork"></a> VSTO 增益集搭配 Microsoft Office 應用程式的運作方式
 當使用者啟動 Microsoft Office 應用程式時，該應用程式會使用部署資訊清單和應用程式資訊清單來尋找並載入最新版的 VSTO 增益集組件。 下圖顯示這些 VSTO 增益集的基本架構。

 ![2007 Office 增益集架構](../vsto/media/office07addin.png "2007 Office 增益集架構")

> [!NOTE]
> 在以 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或 [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]為目標的 Office 方案中，方案會使用內嵌於方案組件中的 PIA 類型資訊來呼叫主應用程式的物件模型，而不是直接呼叫 PIA。 如需詳細資訊，請參閱 [設計和建立 Office 方案](../vsto/designing-and-creating-office-solutions.md)。

### <a name="loading-process"></a>載入處理序
 當使用者啟動應用程式，就會執行下列步驟：

1. 應用程式會檢查可識別使用 Visual Studio 中的 Office Developer Tools 所建立之 VSTO 增益集的登錄項目。

2. 如果應用程式找到這些登錄項目，則會載入 VSTOEE.dll，而 VSTOEE.dll 會載入 VSTOLoader.dll。 這些都是 Visual Studio 2010 Tools for Office Runtime 載入器元件的 Unmanaged DLL。 如需詳細資訊，請參閱 [Visual Studio Tools for Office 執行時間總覽](../vsto/visual-studio-tools-for-office-runtime-overview.md)。

3. *VSTOLoader.dll* 載入 [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] ，並啟動的 managed 部分 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 。

4. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 會檢查資訊清單更新，然後下載最新的應用程式和部署資訊清單。

5. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 會執行一系列的安全性檢查。 如需詳細資訊，請參閱 [安全的 Office 方案](../vsto/securing-office-solutions.md)。

6. 如果 VSTO 增益集受信任而得以執行，則 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 會使用部署資訊清單和應用程式資訊清單來檢查組件更新。 如果有新版的組件可用，執行階段就會將新版的組件下載至用戶端電腦上的 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 快取。 如需詳細資訊，請參閱 [部署 Office 方案](../vsto/deploying-an-office-solution.md)。

7. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 會建立新的應用程式定義域，以便載入 VSTO 增益集組件。

8. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 會將 VSTO 增益集組件載入至此應用程式定義域中。

9. 如果您已覆寫 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 方法，則 <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> 會在您的 VSTO 增益集中呼叫此方法。

     您可以選擇覆寫這個方法，以便將 VSTO 增益集中的物件公開至其他 Microsoft Office 方案。 如需詳細資訊，請參閱 [從其他 Office 方案呼叫 VSTO 增益集](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)的程式碼。

10. 如果您已覆寫 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 方法，則 <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> 會在您的 VSTO 增益集中呼叫此方法。

     您可以選擇覆寫這個方法，傳回實作擴充性介面的物件以擴充 Microsoft Office 功能。 如需詳細資訊，請參閱使用擴充性 [介面自訂 UI 功能](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)。

    > [!NOTE]
    > [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 會針對主應用程式支援的每個擴充性介面，個別呼叫 <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> 方法。 雖然第一次呼叫 <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> 方法通常發生於呼叫 `ThisAddIn_Startup` 方法之前，但 VSTO 增益集不得假設何時將會呼叫 <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> 方法，或將會呼叫的次數。

11. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 會在 VSTO 增益集中呼叫 `ThisAddIn_Startup` 方法。 這個方法是 <xref:Microsoft.Office.Tools.AddInBase.Startup> 事件的預設事件處理常式。 如需詳細資訊，請參閱 [Office 專案中的事件](../vsto/events-in-office-projects.md)。

## <a name="see-also"></a>另請參閱
- [Visual Studio 中的 Office 方案架構](../vsto/architecture-of-office-solutions-in-visual-studio.md)
- [檔層級自訂的架構](../vsto/architecture-of-document-level-customizations.md)
- [Visual Studio Tools for Office 執行時間總覽](../vsto/visual-studio-tools-for-office-runtime-overview.md)
- [程式 VSTO 增益集](../vsto/programming-vsto-add-ins.md)
- [開發 Office 方案](../vsto/developing-office-solutions.md)
- [保護 Office 方案](../vsto/securing-office-solutions.md)
- [部署 Office 方案](../vsto/deploying-an-office-solution.md)

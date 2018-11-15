---
title: Visual Studio Tools for Office runtime 概觀
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office runtime [Office development in Visual Studio], about Office runtime
- VSTOLoader.dll
- runtime loader [Office development in Visual Studio]
- Office runtime [Office development in Visual Studio], assemblies
- Office runtime [Office development in Visual Studio]
- runtime [Office development in Visual Studio], assemblies
- vstoee.dll
- Visual Studio Tools for Office runtime
- Office solutions [Office development in Visual Studio], runtime
- solutions [Office development in Visual Studio], runtime
- versions [Office development in Visual Studio], runtime
- assemblies [Office development in Visual Studio], runtime
- runtime [Office development in Visual Studio], about VSTO runtime
- solution loader [Office development in Visual Studio]
- runtime [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b169242b9828f47f1ecfb87ebf02a9f86234699f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49836992"
---
# <a name="visual-studio-tools-for-office-runtime-overview"></a>Visual Studio Tools for Office runtime 概觀
  若要執行使用 Visual Studio 中的 Microsoft Office developer tools 所建立的解決方案，必須在使用者電腦上安裝 Visual Studio 2010 Tools for Office 執行階段。 如需詳細資訊，請參閱 <<c0> [ 如何： 安裝 Visual Studio Tools for Office runtime 可轉散發套件](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)。 Visual Studio 2010 Tools for Office 執行階段是由兩個主要元件所組成：  
  
- Office Extensions for .NET Framework。 這些元件是 Managed 組件，可提供您的方案與 Microsoft Office 應用程式之間的通訊層。 如需詳細資訊，請參閱 <<c0> [ 了解適用於.NET Framework 的 Office 擴充功能](#officeextensions)。  
  
- Office 方案載入器。 這個元件是一組 Unmanaged DLL，Office 應用程式會使用這組 DLL 來載入執行階段和您的方案。 如需詳細資訊，請參閱 <<c0> [ 了解 Office 方案載入器](#UnmanagedLoader)。  
  
  這個執行階段可以用數種不同的方式安裝。 所安裝的執行階段元件會因進行執行階段安裝時的電腦組態而異。 如需詳細資訊，請參閱 < [Visual Studio Tools for Office runtime 安裝案例](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md)。  
  
##  <a name="officeextensions"></a> 了解適用於.NET Framework 的 Office 擴充功能  
 Visual Studio 2010 Tools for Office runtime 包含 Office 擴充功能適用於.NET Framework 3.5，[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]和更新版本。 以 .NET Framework 的每個版本為目標的方案會使用該版本的適當擴充功能。  
  
 這些擴充功能包含您的方案用來自動化和擴充 Office 應用程式的組件。 當您建立 Office 專案時，Visual Studio 會自動針對專案類型和專案的目標 .NET Framework，加入適用組件的參考。 如需 Office 擴充功能中的組件的詳細資訊，請參閱[在 Visual Studio Tools for Office runtime 的組件](../vsto/assemblies-in-the-visual-studio-tools-for-office-runtime.md)。  
  
### <a name="design-differences-in-the-office-extensions"></a>中的 Office 擴充功能的設計差異  
 您在 Office Extensions for .NET Framework 3.5 中使用的大部分類型是類別。 這些是舊版 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]所含的相同類別。 相較之下，您在適用於 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更新版本的 Office 擴充功能中使用的大部分類型是介面。 例如，如果您以 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更新版本為目標，則 <xref:Microsoft.Office.Tools.Excel.Worksheet> 和 <xref:Microsoft.Office.Tools.Word.Document> 類型就會是介面，而不是類別。  
  
 在大部分情況下，不論您的方案是以 .NET Framework 3.5 還是 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]為目標，在 Office 方案中撰寫的程式碼都會相同。 不過，當您以不同版本的 .NET Framework 為目標時，某些功能會需要不同的程式碼。 如需詳細資訊，請參閱 <<c0> [ 設為.NET Framework 4 或更新版本的移轉 Office 方案](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)。  
  
### <a name="interfaces-in-the-office-extensions-for-the-net-framework-4-or-later"></a>適用於.NET Framework 4 或更新版本的 Office 擴充功能的介面  
 在適用於 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 和更新版本的 Office 擴充功能中，大部分介面無法供使用者程式碼實作。 您可以直接實作的介面，僅限名稱開頭為字母 **I**者，例如 <xref:Microsoft.Office.Tools.Excel.ISmartTagExtension>。  
  
 所有介面，不是以字母**我**由 Visual Studio 2010 Tools for Office runtime 於內部實作，這些介面可能會在未來版本中變更。 若要建立實作這些介面的物件，請使用專案中 `Globals.Factory` 物件提供的方法。 例如，若要取得實作 <xref:Microsoft.Office.Tools.Excel.SmartTag> 介面的物件，請使用 `Globals.Factory.CreateSmartTag` 方法。 如需詳細資訊`Globals.Factory`，請參閱 <<c2> [ 全域存取 Office 專案中的物件](../vsto/global-access-to-objects-in-office-projects.md)。  
  
### <a name="enable-type-equivalence-and-embedded-types-in-projects-that-target-the-net-framework-4-or-later"></a>啟用類型等價和內嵌的類型的.NET Framework 4 或更新版本為目標的專案中  
 由於適用於 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 和更新版本之 Office 擴充功能的物件模型是以介面為基礎，因此您可以在 Visual Studio 中使用 Visual C# 和 Visual Basic 的類型等價功能，從 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 將類型資訊內嵌至方案。 這項功能可讓 Office 方案和 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 分別處理各自的版本。 例如，如果您的方案使用 <xref:Microsoft.Office.Tools.Word.Document> 介面做為內嵌類型，而執行階段的下一個版本將成員加入至 <xref:Microsoft.Office.Tools.Word.Document> 介面，則您的方案仍然可以使用執行階段的下一個版本。 如果方案不使用 <xref:Microsoft.Office.Tools.Word.Document> 介面做為內嵌類型，那麼您的方案將無法再使用執行階段的下一個版本。  
  
 根據預設，當您建立以 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更新版本為目標的 Office 專案時，不會啟用類型等價功能。 如果您要啟用此項功能，請將專案中下列任一組件參考的 [ **內嵌 Interop 類型** ] 屬性設為 [ **True**]：  
  
- Microsoft.Office.Tools.dll  
  
- Microsoft.Office.Tools.Common.dll  
  
- Microsoft.Office.Tools.Excel.dll  
  
- Microsoft.Office.Tools.Outlook.dll  
  
- Microsoft.Office.Tools.Word.dll  
  
  進行此項變更後，當您建置專案時，專案使用之所有執行階段類型的類型資訊都會內嵌至方案組件中。 在執行階段的解決方案會使用內嵌的類型資訊，而不是參考的組件中的類型資訊。  
  
##  <a name="UnmanagedLoader"></a> 了解 Office 方案載入器  
 Visual Studio Tools for Office Runtime 包含 Office 應用程式用來載入執行階段和 Office 方案的數個 Unmanaged DLL。 雖然您應該永遠都不需要直接使用這些 DLL，但是知道這些 DLL 的用途有助於深入了解 Office 方案的架構。  
  
 如需如何在載入過程中使用這些元件的資訊，請參閱[文件層級自訂的架構](../vsto/architecture-of-document-level-customizations.md)並[Architecture of VSTO 增益集](../vsto/architecture-of-vsto-add-ins.md)。  
  
### <a name="vstoeedll"></a>vstoee.dll  
 當使用者開啟文件層級自訂或 VSTO 增益集啟動時，Office 應用程式呼叫*VSTOEE.dll*來執行工作負載所需[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]。  
  
 *VSTOEE.dll*可確保正確的版本[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]載入解決方案和安裝的 Office 版本。 雖然多個版本的[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]可以安裝在同一部電腦，也就是只有一個執行個體*VSTOEE.dll*安裝一次。 這是*VSTOEE.dll* ，已包含最新版本的電腦上安裝的執行階段。 如需不同版本的詳細資訊[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]，可以用於其他方案，請參閱 <<c2> [ 執行不同版本的 Microsoft Office 中的方案](../vsto/running-solutions-in-different-versions-of-microsoft-office.md)。  
  
### <a name="vstoloaderdll"></a>VSTOLoader.dll  
 在後*VSTOEE.dll*載入適當版本的[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]， *VSTOLoader.dll*執行大部分的工作，才能載入方案組件。 *VSTOLoader.dll*達成幾件事：  
  
- 為每個方案組件建立應用程式定義域。  
  
- 執行一組安全性檢查，確認方案組件具有執行權限。  
  
- 載入方案所需的 Office Extensions for .NET Framework 版本。  
  
  *VSTOLoader.dll*也會執行 VSTO 增益集特有的幾件事：  
  
- 實作 <xref:Extensibility.IDTExtensibility2> 介面。 <xref:Extensibility.IDTExtensibility2> 是所有 Microsoft Office 應用程式之 VSTO 增益集都必須實作的 COM 介面。 這個介面定義了應用程式要與 VSTO 增益集通訊時，所呼叫的方法。  
  
- 它會實作 IManagedAddin 介面。 Office 應用程式會使用這個介面協助載入 VSTO 增益集。如需詳細資訊，請參閱 < [IManagedAddin 介面](../vsto/imanagedaddin-interface.md)。  
  
## <a name="understand-the-32-bit-and-64-bit-versions-of-the-runtime"></a>了解的 32 位元和 64 位元版本的執行階段  
 有個別的 64 位元和 32 位元版本的 Visual Studio 2010 Tools for Office 執行階段。 這些執行階段版本可用於執行 64 位元和 32 位元版本 Office 的方案。 下表顯示 Windows 與 Office 的每一種組合所需的執行階段版本。  
  
|Windows 版本|Microsoft Office 版本|Visual Studio Tools for Office Runtime 的所需版本|  
|------------------------|---------------------------------|--------------------------------------------------------------------|  
|32 位元|32 位元|32 位元|  
|64 位元|32 位元|64 位元|  
|64 位元|64 位元|64 位元|  
  
 當您安裝 Office 時，所需的 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 版本會隨 Office 一起安裝。 例如，當您在 64 位元版本 Windows 上安裝 64 位元版本 Office 時，會一併安裝 64 位元版本的 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 。 如需安裝的詳細資訊[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]與 Office，請參閱[Visual Studio Tools for Office runtime 安裝案例](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md)。  
  
 64 位元版本 Office 也能執行以 Visual Studio 2008 中 2007 Microsoft Office System 的專案範本所建立的 Office 方案， 但不能執行以 Visual Studio 2008 中 Microsoft Office 2003 適用之專案範本所建立的 Office 方案，或以 Visual Studio 2005 所建立的 Office 方案。 如需詳細資訊，請參閱 <<c0> [ 執行不同版本的 Microsoft Office 中的方案](../vsto/running-solutions-in-different-versions-of-microsoft-office.md)。  
  
## <a name="repair-the-visual-studio-2010-tools-for-office-runtime"></a>修復 Visual Studio 2010 Tools for Office 執行階段  
 如果您需要修復此執行階段，請在 [控制台] 開啟 [程式和功能]  或 [新增或移除程式]  ，選取程式清單中的 [Microsoft Visual Studio 2010 Tools for Office Runtime]  ，然後按一下 [解除安裝] 。 執行的安裝程式可讓您修復此執行階段。 如果您按一下 [ **變更**]，則系統不會提供修復執行階段的選項。  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio Tools for Office runtime 安裝案例](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md)   
 [在 Visual Studio Tools for Office runtime 的組件](../vsto/assemblies-in-the-visual-studio-tools-for-office-runtime.md)   
 [在 Visual Studio 中的 Office 方案的架構](../vsto/architecture-of-office-solutions-in-visual-studio.md)   
 [文件層級自訂的架構](../vsto/architecture-of-document-level-customizations.md)   
 [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)   
 [如何： 在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [升級和移轉 Office 方案](../vsto/upgrading-and-migrating-office-solutions.md)  
  
  
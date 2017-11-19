---
title: "原始檔控制整合的概觀 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: source control [Visual Studio SDK], about source control
ms.assetid: 3a46e4eb-e677-49c3-8647-d927d035a19a
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ed0ffd44e248cb1f420cb7be308a46c914fffee2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="source-control-integration-overview"></a>原始檔控制整合概觀
本節將比較兩種方式整合到 Visual Studio 的原始檔控制。原始檔控制外掛程式與提供原始檔控制方案，並反白顯示新的原始檔控制功能的 VSPackage。 Visual Studio 可讓您手動切換原始檔控制 Vspackage 和原始檔控制外掛程式，以及自動解決方案為基礎的切換。  
  
## <a name="source-control-integration"></a>原始檔控制整合  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]支援兩種類型的原始檔控制整合選項。 在所有版本的[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，您仍然可以將整合為外掛程式，根據原始檔控制外掛程式 API （先前也稱為 MSSCCI API），可提供基本的原始檔控制功能，同時使用 Visual Studio 原始檔控制使用者介面 （UI)。 原始檔控制 VSPackage，相反地，提供新的、 深層整合[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]適合需求的複雜度，以及在其原始檔控制模型中的自主高層級的原始檔控制整合的路徑。  
  
 ![原始檔控制概觀](../../extensibility/internals/media/sourcectnrloverview.gif "SourceCtnrlOverview")  
  
## <a name="source-control-plug-in"></a>原始檔控制外掛程式  
 所有版本的 Visual Studio 都支援原始檔控制外掛程式 API 1.2 版的規格做為整合路徑。 原始檔控制外掛程式實施者寫入實作原始檔控制整合和註冊的原始檔控制外掛程式 API 函式中所述的 DLL[建立原始檔控制外掛程式](../../extensibility/internals/creating-a-source-control-plug-in.md)。 在這種方式，使用整合式開發環境 (IDE) [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] UI 對話方塊，例如簽入、 簽出、 工具/選項屬性頁面、 工具列和原始檔控制圖像 （glyph）。 原始檔控制外掛程式 API 嚴格遵守確保輕鬆整合到 Visual Studio，並沒有問題的使用者體驗。 這表示原始檔控制外掛程式必須實作的大部分函式和應用程式開發介面中詳述的回呼。  
  
 若要實作原始檔控制外掛程式使用原始檔控制外掛程式 API，請遵循下列步驟：  
  
1.  建立實作中指定的函式的 DLL[原始檔控制外掛程式](../../extensibility/source-control-plug-ins.md)。  
  
2.  藉由適當的登錄項目中註冊的 DLL (述[如何： 安裝原始檔控制外掛程式](../../extensibility/internals/how-to-install-a-source-control-plug-in.md))。  
  
3.  建立協助程式 UI 和提示原始檔控制配接器套件 （處理透過原始檔控制外掛程式的原始檔控制功能的 Visual Studio 元件） 時顯示  
  
 在原始檔控制命令的回應，Visual Studio IDE 呈現的基本作業的標準 UI，並再將資訊傳遞至原始檔控制外掛程式透過原始檔控制外掛程式 API 中定義的函式。 進階選項，請原始檔控制外掛程式上可以呼叫來呈現自己的 UI，例如，瀏覽的原始檔控制的專案。 這表示，使用者可能會看到的兩個可能是不同的 UI 樣式時處理的原始檔控制： Visual Studio 會顯示 UI 和原始檔控制外掛程式呈現 UI。 這是最明顯的進階原始檔控制作業。  
  
### <a name="drawbacks-to-implementing-a-source-control-plug-in"></a>若要實作原始檔控制外掛程式的缺點  
  
-   如需進階的功能，使用者可能會看到兩個不同的樣式的介面，導致可能的混淆。  
  
-   原始檔控制外掛程式會侷限於原始檔控制外掛程式 API 所隱含的原始檔控制模型。  
  
-   原始檔控制外掛程式 API 可能太嚴格，某些原始檔控制案例。  
  
### <a name="advantages-to-implementing-a-source-control-plug-in"></a>若要實作原始檔控制外掛程式的優點  
  
-   Visual Studio 會提供所有基本的原始檔控制作業的所有 UI，讓原始檔控制外掛程式沒有實作可能很複雜的 UI。  
  
-   嚴格的 API，因為原始檔控制外掛程式可以輕易地與外部來源控制程式互動以提供更廣泛的功能。Visual Studio 不在意太遠如何原始檔控制功能完成的只會根據原始檔控制外掛程式 API 來完成。  
  
-   很容易實作原始檔控制外掛程式比原始檔控制 VSPackage。  
  
## <a name="source-control-vspackage"></a>原始檔控制 VSPackage  
 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]可讓深層整合到 Visual Studio 的 Visual Studio 提供的原始檔控制使用者介面完全取代與原始檔控制功能的完整控制權。 原始檔控制 VSPackage 註冊使用 Visual Studio，並提供原始檔控制功能。 雖然可以使用 Visual Studio 中註冊數個原始檔控制的 Vspackage，只有一個可以是作用中一次。 原始檔控制 VSPackage 有 Visual Studio 中的原始檔控制功能和外觀的完整控制權，作用中時。 所有其他原始檔控制系統中可能會註冊的 Vspackage 處於非使用狀態，而且不會完全顯示任何 UI。  
  
 實作 VSPackage 的原始檔控制需要 「 所有或執行任何動作 」 的策略。 原始檔控制 VSPackage 的建立者必須投資花費相當大量的心力實作幾個原始檔控制的介面和新的 UI 項目 （對話方塊、 功能表和工具列） 來涵蓋整個原始檔控制功能。 請參閱[建立原始檔控制 VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md)如需詳細資訊。  
  
### <a name="drawbacks-to-implementing-a-source-control-vspackage"></a>若要實作原始檔控制 VSPackage 的缺點  
  
-   VSPackage 必須實作複雜的介面，以成功地與 Visual Studio 整合的數的字。  
  
-   VSPackage 必須提供原始檔控制; 所需的所有 UIVisual Studio 會提供此區域中的沒有協助。  
  
-   原始檔控制 VSPackage 可感知繫結至 Visual Studio，並不能與獨立程式，以便與原始檔控制程式的外部版本無法輕鬆地共用功能。  
  
### <a name="advantages-to-implementing-a-source-control-vspackage"></a>若要實作原始檔控制 VSPackage 的優點  
  
-   VSPackage 具有完整控制權的原始檔控制 UI 和功能，因為使用者會看到與原始檔控制的無縫式的介面。  
  
-   VSPackage 不會侷限於特定來源控制模型。  
  
## <a name="see-also"></a>另請參閱  
 [原始檔控制](../../extensibility/internals/source-control.md)   
 [建立原始檔控制外掛程式](../../extensibility/internals/creating-a-source-control-plug-in.md)   
 [建立原始檔控制 VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md)   
 [原始檔控制的新功能](../../extensibility/internals/what-s-new-in-source-control.md)
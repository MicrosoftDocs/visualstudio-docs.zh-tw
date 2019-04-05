---
title: 擴充 UML 模型和圖表 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML - extending
- UML model, extending
ms.assetid: b5bfa61e-ea59-4c3b-b5af-53475d7d13cd
caps.latest.revision: 39
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 2c13d30b1657917d55e5d3218c70aa8f2a69ec67
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/26/2019
ms.locfileid: "59000502"
---
# <a name="extend-uml-models-and-diagrams"></a>擴充 UML 模型和圖表
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題摘要說明各種不同方式，可讓您擴充 Visual Studio 隨附的 UML 模型工具。 若要查看支援各種模型類型和工具的 Visual Studio 版本有哪些，請參閱 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)。  
  
 在下列範例案例中，Fabrikam 設計並安裝了機場行李處理系統。 機場專案之間在基本設備與控制的軟體上有許多共通點。 但是其中也有些大相逕庭之處，例如輸送帶的配置、登機報到櫃檯、儲物箱和其他處理行李的設備。  
  
 在新專案起始階段，Fabrikam 小組建立了 UML 模型協助他們與客戶溝通這些需求。 他們使用活動圖表展示行李流程，其中物件節點代表每一項設備。 此 UML 模型不會直接呈現系統的程式碼。  
  
 Fabrikam 的工具小組製作了一系列的增強功能來協助此開發小組。 下列各節描述您可以定義的各種擴充功能。 您可以將多項技術合併成單一 Visual Studio 擴充功能。  
  
 如需詳細資訊，請參閱這段影片中：![影片連結](../data-tools/media/playvideo.gif "PlayVideo")[MSDN 「 如何 」 系列：UML 工具和擴充性](http://go.microsoft.com/fwlink/?LinkId=214467)。  
  
##  <a name="Requirements"></a> 需求  
  
-   [Visual Studio SDK](../extensibility/visual-studio-sdk.md)。  
  
-   [Modeling SDK for Visual Studio 2015](http://www.microsoft.com/download/details.aspx?id=48148)。  
  
## <a name="profiles"></a>設定檔  
 設定檔可讓您定義 UML 項目的造型和其他屬性。  
  
 Fabrikam 的工具開發人員在活動圖表的物件節點上定義造型，例如「輸送帶」和「登機報到櫃檯」。 當小組成員使用活動圖表建立行李處理配置時，就能夠設定造型來表示每一個節點所代表的設備類型。 工具開發人員在部分造型上定義了額外的屬性，讓使用者能夠記錄值，例如輸送帶容量以及登機報到櫃檯的慣用側。  
  
 如需詳細資訊，請參閱 <<c0> [ 定義要擴充 UML 的設定檔](../modeling/define-a-profile-to-extend-uml.md)。  
  
## <a name="custom-toolbox-items"></a>自訂工具箱項目  
 自訂工具箱項目可從您在圖表中定義的原型建立項目或項目群組。 例如，您可以建立以特定色彩或造型建立使用案例的工具，或是代表設計模式的類別和關聯群組。 您可以將這些工具箱項目加入 Visual Studio 擴充功能中，並且散發給其他使用者。  
  
 如需詳細資訊，請參閱 <<c0> [ 定義自訂模型工具箱項目](../modeling/define-a-custom-modeling-toolbox-item.md)。  
  
## <a name="validation"></a>驗證  
 您可以定義規則，確保 UML 模型符合指定的條件約束。  
  
 Fabrikam 的工具開發人員會定義規則，協助小組成員在行李處理模型中避開簡單的錯誤。 例如，登機報到櫃檯無法直接連接到儲物箱。 兩者之間必須至少有一條輸送帶。  
  
 如需詳細資訊，請參閱 <<c0> [ 定義 UML 模型的驗證條件約束](../modeling/define-validation-constraints-for-uml-models.md)。  
  
## <a name="menu-commands"></a>功能表命令  
 您可以定義使用者以滑鼠右鍵按一下 UML 圖表上的項目即可叫用的命令。 這些命令可以更新該模型和圖表，或在 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]中執行其他作業。  
  
 Fabrikam 定義了功能表命令來自動化經常執行的作業，例如建立登機報到櫃檯並將它連接到選取的輸送帶，或根據公司的配置規則重新排列圖表。  
  
 請參閱[在模型圖上定義功能表命令](../modeling/define-a-menu-command-on-a-modeling-diagram.md)。  
  
## <a name="gestures"></a>軌跡  
 您可以定義使用者按兩下圖表項目即可啟始的命令，或是拖曳到圖表或圖表的項目上即可啟始的命令。 您還可以定義命令來處理拖曳自其他 UML 圖表或 Visual Studio 的其他組件之項目，或是拖曳自其他應用程式或 Windows 檔案總管 (或檔案總管) 的項目。  
  
 Fabrikam 小組成員可將檔案 (例如規格) 與任何模型項目產生關聯，只要從 Windows 桌面拖曳即可。 工具開發人員定義了造型，提供任何含有檔案路徑屬性的項目，以及在檔案放置到項目時設定造型和檔案路徑的軌跡。  
  
 如需詳細資訊，請參閱 <<c0> [ 在模型圖上定義軌跡處理常式](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md)。  
  
## <a name="responding-to-changes"></a>回應變更  
 您可以撰寫程式碼，回應模型中不論是使用者動作或其他程式碼所造成的變更。  
  
 Fabrikam 的開發人員建立程式碼，根據造型自動設定項目的色彩。 這讓使用者更容易區別模型中項目所扮演的不同角色。  
  
 如需詳細資訊，請參閱[如何：回應 UML 模型中的變更](../misc/how-to-respond-to-changes-in-a-uml-model.md)。  
  
## <a name="model-bus"></a>模型匯流排  
 「模型匯流排」可讓您從另一個圖表或另一個 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] 擴充功能存取圖表或模型。 除此之外，您還可以將資訊散佈至多個模型，讓許多人能夠同時在合併的模型上執行工作。  
  
 Fabrikam 使用活動圖表上的項目表示行李處理設備。 每一個設備項目都可以在另一個圖表上擁有更詳細的規格，而該圖表可以位於另一個模型上。 行李流程圖上的驗證條件約束可從其他圖表擷取此設備的相關屬性。 其他圖表的參考會儲存在造型中定義的其他屬性中。  
  
 如需詳細資訊，請參閱 <<c0> [ 整合 UML 模型與其他模型及工具](../modeling/integrate-uml-models-with-other-models-and-tools.md)。  
  
## <a name="generation"></a>產生  
 從模型可以產生程式碼、指令碼、組態、文件、新模型或其他成品。  
  
 在 Fabrikam 設計的行李系統中，專案之間大部分的程式碼都相同。 主要變動的部分是機場內行李流程的計劃。 設計小組有了前幾個專案的經驗後，工具開發人員就會建立範本，該範本會從行李流程模型產生大部分變動程式碼和其他檔案 (例如使用者文件)。 這樣可大幅縮短每一個新專案的開發時間並降低錯誤率。  
  
 如需詳細資訊，請參閱 <<c0> [ 從 UML 模型產生檔案](../modeling/generate-files-from-a-uml-model.md)。  
  
## <a name="team-foundation-server-integration"></a>Team Foundation Server 整合  
 您可以將工作項目連結至模型項目，並且以程式設計方式存取連結的項目。  
  
 Fabrikam 的工具開發人員為每一個機場專案撰寫了產生工作排程的工具。 在此排程中的工作項目會連結到模型項目。  
  
 如需詳細資訊，請參閱 <<c0> [ 定義工作項目連結處理常式](../modeling/define-a-work-item-link-handler.md)。  
  
## <a name="tools-that-update-models"></a>更新模型的工具  
 您可以建立能夠載入 UML 模型的獨立應用程式和 Visual Studio 擴充功能。  
  
 Fabrikam 的開發人員建立了讀取模型和產生每一個模型項目之工作進度報告的工具。  
  
 如需詳細資訊，請參閱 <<c0> [ 讀取程式碼中的 UML 模型](../modeling/read-a-uml-model-in-program-code.md)。  
  
## <a name="domain-specific-languages"></a>特定領域語言  
 如果您經常使用特定類型的模型，建立特定領域語言可能會對您有所幫助。 相較於 UML 模型，建立此工具將可讓您更貼近商務需求，但也需付出更多心力在建置和維護上。 如需詳細資訊，請參閱 < [Modeling SDK for Visual Studio-特定領域語言](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)。  
  
## <a name="external-resources"></a>外部資源  
  
|**分類**|**連結**|  
|------------------|---------------|  
|**影片**|![影片連結](../data-tools/media/playvideo.gif "PlayVideo") [MSDN 「 如何 」 系列：UML 工具和擴充性](http://go.microsoft.com/fwlink/?LinkId=214467)<br /><br /> ![影片連結](../data-tools/media/playvideo.gif "PlayVideo") [Channel 9:使用 Visual Studio 的 UML](http://go.microsoft.com/fwlink/?LinkId=199957)|  
|**論壇**|-   [Visual Studio Visualization & Modeling Tools](http://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [Visual Studio Visualization & Modeling SDK (DSL 工具)](http://go.microsoft.com/fwlink/?LinkId=184721)|  
|**部落格**|[Visual Studio ALM + Team Foundation Server 部落格](http://go.microsoft.com/fwlink/?LinkID=201340)|  
|**技術文件和日誌**|[MSDN 架構中心](http://go.microsoft.com/fwlink/?LinkId=201343)|  
  
## <a name="see-also"></a>另請參閱  
 [建立應用程式模型](../modeling/create-models-for-your-app.md)   
 [UML 模型擴充性的 API 參考](../modeling/api-reference-for-uml-modeling-extensibility.md)

---
title: 選項對話方塊、專案和方案 | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Projects and Solutions Options dialog box
- Options dialog box, Projects and Solutions
ms.assetid: 2801f24e-a138-488a-ae3c-e1f99a678ac0
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6999a8af211fec07e50eac006e7de7bb11f49418
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47489849"
---
# <a name="projects-and-solutions-options-dialog-box"></a>專案和方案、選項對話方塊
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

本主題的最新的版本可從[專案和方案、 選項對話方塊](https://docs.microsoft.com/visualstudio/ide/reference/projects-and-solutions-options-dialog-box)。  
  
  
隨著專案的開發和建置，設定 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 專案資料夾的預設路徑，並決定 [輸出] 視窗、[工作清單] 和方案總管的預設行為。 若要存取這個對話方塊，請按一下 [工具]/[選項]，並展開 [專案和方案]，然後按一下 [一般]。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊可用選項，以及功能表命令的名稱和位置，可能會與 [說明] 中描述的有所不同。 撰寫這個說明網頁時，會考慮到 [一般開發設定]。 若要檢視或變更您的設定，請選擇 [工具] 功能表上的 [匯入和匯出設定]。 如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)  
  
## <a name="settings"></a>設定  
 **專案位置**  
 設定要建立新專案和方案資料夾及目錄的預設位置。 許多對話方塊也會使用此選項所設定的位置當成資料夾起始點。 例如，[開啟專案] 對話方塊使用此位置當成 [我的專案] 捷徑。  
  
 **使用者專案範本位置**  
 設定 [新增專案] 對話方塊用來建立 [我的範本] 清單的預設位置。 如需詳細資訊，請參閱[如何：尋找並整理範本](../../ide/how-to-locate-and-organize-project-and-item-templates.md)。  
  
 **使用者項目範本位置**  
 設定 [新增項目] 對話方塊用來建立 [我的範本] 清單的預設位置。 如需詳細資訊，請參閱[如何：尋找並整理範本](../../ide/how-to-locate-and-organize-project-and-item-templates.md)。  
  
 **建置完成但發生錯誤時一律顯示錯誤清單**  
 只有在無法建置專案時，才在建置完成時開啟 [錯誤清單]。 這樣會顯示在建置過程中發生的錯誤。 清除此選項時，仍然會發生錯誤，但是建置完成時不會開啟視窗。 這個選項預設為啟用。  
  
 **在 [方案總管] 中追蹤使用中的項目**  
 選取此選項時，方案總管會自動開啟並選取使用中的項目。 隨著您使用專案或方案中的不同檔案，或設計工具中的不同元件，選取的項目也會變更。 如果清除這個選項，方案總管中的選取項目就不會自動變更。 這個選項預設為啟用。  
  
 **顯示進階組建組態**  
 選取此選項時，[專案屬性頁] 對話方塊和 [方案屬性頁] 對話方塊就會顯示組建組態選項。 清除此選項時，[!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 與 [!INCLUDE[csprcs](../../includes/csprcs-md.md)] 專案 (包含一或兩個組態偵錯和發行) 的 [專案屬性頁] 對話方塊和 [方案屬性頁] 對話方塊就不會顯示組建組態選項。 如果專案具有使用者定義的組態，就會顯示建置組態選項。  
  
 取消選取此選項時，[建置] 功能表上的命令 (例如 [建置方案]、[重建方案] 及 [清除方案]) 會在發行組態上執行，而 [偵錯] 功能表上的命令 (例如 [開始偵錯] 及 [啟動但不偵錯]) 則會在偵錯組態上執行。  
  
 **一律顯示方案**  
 選取此選項時，IDE 一律會顯示方案以及針對方案執行的所有命令。 清除此選項時，所有專案都會建立為獨立專案；如果方案只包含一個專案，您就不會在 [方案總管] 中看到方案，也不會在 IDE 中看到針對方案執行的命令。  
  
 **在建立新專案時予以儲存**  
 選取此選項時，您可以在 [新增專案] 對話方塊中指定專案的位置。 清除此選項時，所有新專案都會建立為暫存專案。 當您使用暫存專案時，可以建立和測試專案，而不需要指定磁碟位置。  
  
 **專案位置未受信任時警告使用者**  
 如果您嘗試在未受完全信任的位置建立新專案或開啟現有專案 (例如，在 UNC 路徑或 HTTP 路徑上)，則會顯示訊息。 使用此選項，指定每當您在未受完全信任的位置嘗試建立或開啟專案時，是否要顯示訊息。  
  
 **建置開始時顯示輸出視窗**  
 開始建置方案時，自動在 IDE 中顯示 [輸出] 視窗。 如需詳細資訊，請參閱[如何：控制輸出視窗](http://msdn.microsoft.com/library/91aebd15-8854-4a7a-9f7d-57376fb4e858)。 這個選項預設為啟用。  
  
 **重新命名檔案時提示符號重新命名**  
 選取此選項時，會顯示訊息方塊，詢問是否 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 也應重新命名專案中所有對程式碼元素的參考。  
  
## <a name="see-also"></a>另請參閱  
 [選項對話方塊、專案和方案、建置並執行](../../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md)




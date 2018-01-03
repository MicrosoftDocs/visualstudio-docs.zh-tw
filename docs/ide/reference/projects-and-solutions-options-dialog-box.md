---
title: "選項對話方塊、專案和方案 | Microsoft Docs"
ms.custom: 
ms.date: 07/14/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Projects.General
- VS.ToolsOptionsPages.Projects.Locations
helpviewer_keywords:
- Projects and Solutions Options dialog box
- Options dialog box, Projects and Solutions
ms.assetid: 2801f24e-a138-488a-ae3c-e1f99a678ac0
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: d7b122c66c4fd49cbc8939e5770c56fe8bc48b78
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="projects-and-solutions-options-dialog-box"></a>專案和方案、選項對話方塊
設定與專案和解決方案有關的 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 行為。 若要存取這些選項，請選取 [工具] > [選項] 來展開 [專案和方案]，然後按一下 [一般]。

專案和範本資料夾的預設路徑會透過相同對話方塊中的 [位置] 索引標籤進行設定。
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊可用選項，以及功能表命令的名稱和位置，可能會與 [說明] 中描述的有所不同。 撰寫這個說明網頁時，會考慮到 [一般開發設定]。 若要檢視或變更您的設定，請選擇 [工具] 功能表上的 [匯入和匯出設定]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](../../ide/personalizing-the-visual-studio-ide.md)。  
  
## <a name="general-tab-options"></a>[一般] 索引標籤選項

**建置完成但發生錯誤時一律顯示錯誤清單**  
只有在無法建置專案時，才在建置完成時開啟 [錯誤清單]。 這樣會顯示在建置過程中發生的錯誤。 清除此選項時，仍然會發生錯誤，但是建置完成時不會開啟視窗。 這個選項預設為啟用。  

**在 [方案總管] 中追蹤使用中的項目**  
選取此選項時，方案總管會自動開啟並選取使用中的項目。 隨著您使用專案或方案中的不同檔案，或設計工具中的不同元件，選取的項目也會變更。 如果清除這個選項，方案總管中的選取項目就不會自動變更。 這個選項預設為啟用。  

**顯示進階組建組態**  
選取此選項時，[專案屬性頁] 對話方塊和 [方案屬性頁] 對話方塊就會顯示組建組態選項。 清除此選項時，[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 與 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] 專案 (包含一或兩個組態偵錯和發行) 的 [專案屬性頁] 對話方塊和 [方案屬性頁] 對話方塊就不會顯示組建組態選項。 如果專案具有使用者定義的組態，就會顯示建置組態選項。  

取消選取此選項時，[建置] 功能表上的命令 (例如 [建置方案]、[重建方案] 及 [清除方案]) 會在發行組態上執行，而 [偵錯] 功能表上的命令 (例如 [開始偵錯] 及 [啟動但不偵錯]) 則會在偵錯組態上執行。  

**一律顯示方案**  
選取此選項時，IDE 一律會顯示方案以及針對方案執行的所有命令。 清除此選項時，所有專案都會建立為獨立專案；如果方案只包含一個專案，您就不會在 [方案總管] 中看到方案，也不會在 IDE 中看到針對方案執行的命令。  

**在建立新專案時予以儲存**  
選取此選項時，您可以在 [新增專案] 對話方塊中指定專案的位置。 清除此選項時，所有新專案都會建立為暫存專案。 當您使用暫存專案時，可以建立和測試專案，而不需要指定磁碟位置。  

**專案位置未受信任時警告使用者**  
如果您嘗試在未受完全信任的位置建立新專案或開啟現有專案 (例如，在 UNC 路徑或 HTTP 路徑上)，則會顯示訊息。 使用此選項，指定每當您在未受完全信任的位置嘗試建立或開啟專案時，是否要顯示訊息。  

**建置開始時顯示輸出視窗**  
開始建置方案時，自動在 IDE 中顯示 [輸出] 視窗。 如需詳細資訊，請參閱[如何：控制輸出視窗](http://msdn.microsoft.com/Library/91aebd15-8854-4a7a-9f7d-57376fb4e858)。

**重新命名檔案時提示符號重新命名**  
選取時，[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 會顯示訊息方塊，詢問是否也應重新命名專案中所有對程式碼項目的參考。  

**將檔案移動到新位置前先提示**  
選取時，在方案總管中執行檔案的位置變更前，[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 會顯示確認訊息方塊。 

## <a name="locations-tab-options"></a>[位置] 索引標籤選項

**專案位置**  
指定 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 建立新專案和解決方案資料夾的預設位置。 許多對話方塊也會使用此選項所設定的位置當成資料夾起始點。 例如，[開啟專案] 對話方塊使用此位置當成 [我的專案] 捷徑。  

**使用者專案範本位置**  
指定 [新增專案] 對話方塊用來建立 [我的範本] 清單的預設位置。 如需詳細資訊，請參閱[如何：尋找並整理範本](../../ide/how-to-locate-and-organize-project-and-item-templates.md)。  

**使用者項目範本位置**  
指定 [新增新項目] 對話方塊用來建立 [我的範本] 清單的預設位置。 如需詳細資訊，請參閱[如何：尋找並整理範本](../../ide/how-to-locate-and-organize-project-and-item-templates.md)。 

## <a name="see-also"></a>請參閱  
- [選項對話方塊、專案和方案、建置並執行](../../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md)  
- [選項對話方塊、專案和解決方案、Web 專案](../../ide/reference/options-dialog-box-projects-and-solutions-web-projects.md)
---
title: "設計 XML 命令資料表 (。Vsct) 檔案 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSCT files, designing
ms.assetid: bb87a322-bac4-4258-92bc-9a876f05d653
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: e007ffe8cf3cc893bc9575a3e7c083090b523467
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="designing-xml-command-table-vsct-files"></a>設計 XML 命令資料表 (。Vsct) 檔案
XML 命令表 (.vsct) 檔案描述的配置和外觀 VSPackage 的命令項目。 命令項目包括按鈕、 下拉式方塊、 功能表、 工具列和命令項目群組。 本主題描述 XML 命令資料表檔、 它們如何影響命令項目和功能表，以及如何建立它們。  
  
## <a name="commands-menus-groups-and-the-vsct-file"></a>命令、 功能表、 群組和.vsct 檔  
 .vsct 檔會組織周圍命令、 功能表和命令群組。 .Vsct 檔中的 XML 標記代表每個這些項目，以及其他相關聯的項目，例如命令按鈕、 命令位置和點陣圖。  
  
 當您建立新的 VSPackage 執行[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]封裝範本，範本會產生.vsct 檔的必要項目，功能表命令、 工具視窗中，或自訂編輯器中，根據您的選項。 然後可以修改這個.vsct 檔案，才能符合特定 VSPackage 的需求。 如何修改.vsct 檔案範例，請參閱中的範例[擴充的功能表和命令](../../extensibility/extending-menus-and-commands.md)。  
  
 若要建立新的空白.vsct 檔案時，請參閱[How to： 建立。Vsct 檔案](../../extensibility/internals/how-to-create-a-dot-vsct-file.md)。 一旦建立之後，您加入 XML 項目、 屬性和值來描述命令項目配置的檔案。 詳細的 XML 結構描述，請參閱[VSCT XML 結構描述參考](../../extensibility/vsct-xml-schema-reference.md)。  
  
## <a name="differences-between-ctc-and-vsct-files"></a>.Ctc 和.vsct 檔之間的差異  
 為那些現在已被取代.ctc 檔格式.vsct 檔中的 XML 標記背後的意義都是相同的而他們的實作會稍有不同。  
  
-   新 **\<extern >**標記是您用來參考其他的.h 檔案進行編譯，例如用於[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]工具列。  
  
-   雖然.vsct 檔案支援**/ 包含**陳述式，.ctc 檔一樣，它也提供功能的新\<**匯入 >**項目。 差別在於**/ 包含**帶來**所有**的資訊，但\<**匯入 >**帶來只有名稱中。  
  
-   雖然.ctc 檔需要您在其中定義您的前置處理器指示詞的標頭檔，其中一個不需要.vsct 檔案。 相反地，將您的指示詞放在符號表中，位於**\<符號 >**項目，位於.vsct 檔案最下方。  
  
-   .vsct 檔案功能**\<註解 >**標記，可讓您內嵌任何您喜歡，例如資訊或甚至是圖片的資訊。  
  
-   值會儲存為項目上的屬性。  
  
-   可以儲存在個別或堆疊命令旗標。  Intellisense，不過，不適用於堆疊的命令旗標。 如需命令旗標的詳細資訊，請參閱[命令旗標的項目](../../extensibility/command-flag-element.md)。  
  
-   您可以指定多個類型，例如分割下拉式清單、 組合等等。  
  
-   未驗證的 Guid。  
  
-   每個 UI 項目具有與它所顯示的文字表示的字串。  
  
-   父代是選擇性的。 如果省略，則會使用 「 群組不明 」 的值。  
  
-   圖示引數是選擇性的。  
  
-   檔案 [點陣圖] 區段-.ctc 相同，不同之處在於您現在可以指定檔案名稱，透過提取它會由 vsct.exe 編譯器在編譯時期的 href。  
  
-   ResID-舊點陣圖資源識別碼可以使用，並仍然運作方式相同，如.ctc 檔所示。  
  
-   HRef-新方法，可讓您指定點陣圖資源的檔案名稱。 它會假設所有會使用，所以您可以忽略使用 > 一節。 編譯器會先搜尋本機資源的檔案，然後在任何網路共用資料夾，並定義/I 參數的任何資源。  
  
-   您不再需要 Keybinding-指定模擬器。 如果您指定其中一個，編譯器會假設編輯器和模擬器都相同。  
  
-   已經卸除 Keychord。 Key1、 Mod1、 Key2、 Mod2 新格式。  您可以指定字元、 十六進位、 或 VK 常數。  
  
 新編譯器，vsct.exe，編譯.ctc 和.vsct 檔。 舊的 ctc.exe 編譯器，不過，會辨識都編譯.vsct 檔。  
  
 您可以使用 vsct.exe 編譯器，將現有的.cto 檔轉換.vsct 檔。 如需詳細資訊，請參閱[How to： 建立。從現有的 Vsct 檔案。Cto 檔案](../../extensibility/internals/how-to-create-a-dot-vsct-file.md#how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file)。  
  
## <a name="the-vsct-file-elements"></a>.Vsct 檔項目  
 命令資料表具有下列階層和項目：  
  
 [CommandTable 元素](../../extensibility/commandtable-element.md)— 表示所有的命令、 功能表群組與相關聯 VSPackage 的功能表。  
  
 [Extern 元素](../../extensibility/extern-element.md)— 參考任何您想要與.vsct 檔案合併的外部.h 檔案。  
  
 [包含項目](../../extensibility/include-element.md)— 參考您要編譯 your.vsct 檔案以及任何其他標頭 (.h) 檔案。 .Vsct 檔可以包含.h 檔案包含定義命令、 功能表群組和功能表提供 IDE 或另一個 VSPackage 的常數。  
  
 [命令元素](../../extensibility/commands-element.md)— 表示所有的個別可執行的命令。 每個命令有下列四個子項目：  
  
 [功能表項目](../../extensibility/menus-element.md)— 表示所有的功能表和工具列，在 VSPackage 中的。 功能表會針對命令群組的容器。  
  
 [群組項目](../../extensibility/groups-element.md)— 代表所有在 VSPackage 中的群組。 群組是個別命令的集合。  
  
 [按鈕項目](../../extensibility/buttons-element.md)— 表示所有的命令按鈕，在 VSPackage 中的功能表項目。 按鈕是可以與命令相關聯的視覺控制項。  
  
 [點陣圖項目](../../extensibility/bitmaps-element.md)— 表示所有所有的按鈕，在 VSPackage 中的點陣圖。 點陣圖是顯示下一步或命令按鈕，視內容而定的圖片。  
  
 [CommandPlacements 元素](../../extensibility/commandplacements-element.md)— 表示額外的位置，其中個別的命令應該要位於 VSPackage 的功能表。  
  
 [VisibilityConstraints 元素](../../extensibility/visibilityconstraints-element.md)-指定是否命令會顯示所有時間，或只在特定內容，例如特定對話方塊或視窗會顯示。 只在指定的內容為作用中時，會顯示功能表和命令的值，這個項目的。 預設行為是以隨時顯示命令。  
  
 [金鑰繫結項目](../../extensibility/keybindings-element.md)— 指定命令的任何索引鍵繫結。 也就是說，一個或多個索引鍵組合必須按下執行的命令，例如**CTRL + S**。  
  
 [UsedCommands 元素](../../extensibility/usedcommands-element.md)— Informs[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]環境雖然指定的命令由其他程式碼中，實作，使用目前的 VSPackage 時，它會提供命令的實作。  
  
 `Symbols Element`包含的符號名稱和所有您在封裝中的命令的 GUID 識別碼。  
  
## <a name="vsct-file-design-guidelines"></a>.Vsct 檔案設計指導方針  
 若要成功設計.vsct 檔，請遵循這些指導方針。  
  
-   命令可以只能放置在群組、 群組只能置於功能表和功能表可以放置只在群組中。 只有功能表會實際顯示在 IDE 中，群組並沒有命令。  
  
-   子功能表不能直接指派給功能表上，但必須指派給群組，接著指派給功能表。  
  
-   命令、 子功能表和群組可以指派至一個父代的群組或使用其定義的指示詞的父欄位的功能表。  
  
-   組織等作業只透過在指示詞的父欄位的命令資料表有相當大的限制。 定義物件的指示詞只能取用一個父系引數。  
  
-   重複使用的命令、 群組或子功能表需要新的指示詞，以建立物件的新執行個體，其使用`GUID:ID`組。  
  
-   每個`GUID:ID`組必須是唯一的。 重複使用的命令，例如，已放在功能表上，工具列，或在內容功能表上，由<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>介面。  
  
-   命令和子功能表也可以指派給多個群組，而且您可以指派群組到使用多個功能表[Commands 元素](../../extensibility/commands-element.md)。  
  
## <a name="vsct-file-notes"></a>.Vsct 檔案資訊  
 如果.vsct 檔之後，您同時進行編譯，並且將它放在原生附屬 DLL 中進行任何變更，您應該執行**devenv.exe /setup /nosetupvstemplates**。 這樣會強制在實驗登錄，以可讀取及描述內部資料庫中指定的 VSPackage 資源[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]重建。  
  
 在開發期間，可能會建立並登錄會造成混淆混亂的情形在 IDE 中可能會導致在實驗登錄區中的多個 VSPackage 專案。 若要修正此問題，您可以重實驗登錄區設為預設設定，以移除所有已註冊的 Vspackage 和可能 ide 所做的變更。 若要重設在實驗登錄區，請使用 CreateExpInstance.exe 工具隨附於 Visual Studio SDK。 您可以找到它在  
  
 **%Programfiles (x86) %\Visual Studio\<版本 > SDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe**  
  
 使用命令列執行工具**CreateExpInstance /Reset**。 請記住，此工具會移除在實驗登錄區通常不會安裝的所有已註冊的 Vspackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
## <a name="see-also"></a>請參閱  
 [擴充功能表和命令](../../extensibility/extending-menus-and-commands.md)
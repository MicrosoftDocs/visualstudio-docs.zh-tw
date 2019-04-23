---
title: 設計 XML 命令資料表 (。Vsct) 檔案 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, designing
ms.assetid: bb87a322-bac4-4258-92bc-9a876f05d653
caps.latest.revision: 28
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 987536af051de4a66b3eccadb105fd98455ddf06
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60085899"
---
# <a name="designing-xml-command-table-vsct-files"></a>設計 XML 命令資料表 (。Vsct) 檔案
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

XML 命令表 (.vsct) 檔案描述的版面配置和外觀 VSPackage 的命令項目。 命令的項目包括按鈕、 下拉式方塊、 功能表、 工具列和命令項目的群組。 本主題說明 XML 命令表檔案、 它們如何影響命令的項目和功能表，以及如何加以建立。  
  
## <a name="commands-menus-groups-and-the-vsct-file"></a>命令、 功能表、 群組和.vsct 檔  
 .vsct 檔會組織周圍命令、 功能表和命令群組。 .Vsct 檔案中的 XML 標記代表每個這些項目，以及其他相關聯的項目，例如命令按鈕、 命令位置與點陣圖。  
  
 當您建立新的 VSPackage 執行[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]封裝範本，範本會產生.vsct 檔的必要項目與功能表命令、 工具視窗中，或自訂編輯器中，視您的選擇而定。 然後可以修改此.vsct 檔案，以符合特定 VSPackage 的需求。 如需如何修改.vsct 檔案的範例，請參閱中的範例[擴充的功能表和命令](../../extensibility/extending-menus-and-commands.md)。  
  
 若要建立新的空白.vsct 檔案時，請參閱[How to:建立。Vsct 檔案](../../extensibility/internals/how-to-create-a-dot-vsct-file.md)。 建立之後，您加入 XML 項目、 屬性和值來描述命令項目配置的檔案。 詳細的 XML 結構描述，請參閱 < [VSCT XML Schema Reference](../../extensibility/vsct-xml-schema-reference.md)。  
  
## <a name="differences-between-ctc-and-vsct-files"></a>.Ctc 和.vsct 檔之間的差異  
 雖然為中現在已被取代.ctc 檔格式.vsct 檔案中的 XML 標記背後的意義都是相同的其實作會有點不同。  
  
- 新 **\<extern >** 標記是您用來參考其他的.h 檔案進行編譯，例如[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]工具列。  
  
- 雖然.vsct 檔案支援 **/include**陳述式，.ctc 檔一樣，它也擁有全新\<**匯入 >** 項目。 差別在於**包含**帶入**所有**的資訊，但\<**匯入 >** 帶入只有名稱。  
  
- 雖然.ctc 檔需要您在其中定義您的前置處理器指示詞的標頭檔，其中一個不需要.vsct 檔案。 相反地，將您的指示詞放在符號表中，位於**\<符號 >** 項目，位於.vsct 檔的底部。  
  
- .vsct 檔案功能**\<註釋 >** 標記，可讓您內嵌任何您喜歡，例如資訊或甚至是圖片的資訊。  
  
- 值會儲存為項目上的屬性。  
  
- 可以儲存個別或堆疊命令旗標。  Intellisense，不過，不適用於堆疊的命令旗標。 如需有關命令旗標的詳細資訊，請參閱[Command Flag 元素](../../extensibility/command-flag-element.md)。  
  
- 您可以指定多個類型，例如分割下拉式清單、 combos 等等。  
  
- 未驗證的 Guid。  
  
- 每個 UI 項目具有與它所顯示的文字表示的字串。  
  
- 父代是選擇性的。 如果省略，則會使用 「 群組不明 」 的值。  
  
- 圖示引數是選擇性的。  
  
- 檔案 [點陣圖] 區段-.ctc 相同，不同之處在於您現在可以指定檔案名稱，透過將 vsct.exe 編譯器提取，在編譯時期的 href。  
  
- ResID-舊的點陣圖資源識別碼可用，而且仍然運作方式相同，如.ctc 檔所示。  
  
- HRef-新的方法，可讓您指定點陣圖資源的檔案名稱。 它會假設所有會使用，因此您可以略過使用的區段。 編譯器會先搜尋本機資源的檔案，然後在任何網路共用，以及/I 參數所定義的任何資源。  
  
- 按鍵繫結關係，您不必指定模擬器。 如果您指定其中一個，編譯器會假設編輯器和模擬器都相同。  
  
- 已經卸除 Keychord。 新的格式是 Key1、 Mod1、 Key2、 Mod2。  您可以指定字元、 十六進位或 VK 常數。  
  
  新的編譯器、 vsct.exe，編譯.ctc 和.vsct 檔。 舊的 ctc.exe 編譯器，不過，將不辨識或編譯.vsct 檔。  
  
  您可以將現有的.cto 檔轉換成.vsct 檔使用 vsct.exe 編譯器所在。 如需詳細資訊，請參閱[How to:建立。從現有的 Vsct 檔案。Cto 檔案](../../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file.md)。  
  
## <a name="the-vsct-file-elements"></a>.Vsct 檔項目  
 命令資料表具有下列階層和項目：  
  
 [CommandTable 元素](../../extensibility/commandtable-element.md)— 表示所有的命令、 功能表群組和 VSPackage 相關聯的功能表。  
  
 [Extern 元素](../../extensibility/extern-element.md)-參考任何您想要合併.vsct 檔的外部的.h 檔案。  
  
 [包含項目](../../extensibility/include-element.md)-參考任何您想要編譯以及 your.vsct 檔案的其他標頭 (.h) 檔案。 .Vsct 檔可以包含.h 檔案包含定義命令、 功能表群組和功能表的 IDE 或另一個 VSPackage 提供的常數。  
  
 [命令元素](../../extensibility/commands-element.md)— 表示所有的個別可執行的命令。 每個命令有下列 4 個子元素：  
  
 [功能表項目](../../extensibility/menus-element.md)— 表示所有的功能表和工具列在 VSPackage 中的。 功能表是容器群組的命令。  
  
 [群組項目](../../extensibility/groups-element.md)— 代表所有在 VSPackage 中的群組。 群組為個別命令的集合。  
  
 [按鈕項目](../../extensibility/buttons-element.md)— 表示的所有命令按鈕和功能表項目，在 VSPackage 中的。 按鈕是可以與命令相關聯的視覺控制項。  
  
 [Bitmaps 元素](../../extensibility/bitmaps-element.md)— 表示所有為所有的按鈕，在 VSPackage 中的點陣圖。 點陣圖是顯示旁，或在 [命令] 按鈕，視內容而定的圖片。  
  
 [CommandPlacements 元素](../../extensibility/commandplacements-element.md)— 表示額外的位置，其中個別的命令應該要位於功能表的 VSPackage。  
  
 [VisibilityConstraints 元素](../../extensibility/visibilityconstraints-element.md)-指定是否命令會顯示所有時間，或只在特定內容中，例如特定的對話方塊或視窗會顯示。 功能表和命令的值，這個項目會顯示指定的內容為作用中時，才。 預設行為是以隨時顯示命令。  
  
 [KeyBindings 元素](../../extensibility/keybindings-element.md)— 指定命令的任何索引鍵繫結。 也就是一或多個按鍵組合，必須執行的命令，例如按下**CTRL + S**。  
  
 [UsedCommands 元素](../../extensibility/usedcommands-element.md)— Informs[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]環境雖然指定的命令由其他程式碼中，實作，使用目前的 VSPackage 時，它會提供命令的實作。  
  
 `Symbols Element` 包含的符號名稱和所有您在封裝中的命令的 GUID 識別碼。  
  
## <a name="vsct-file-design-guidelines"></a>.Vsct 檔的設計指導方針  
 若要成功設計.vsct 檔，請遵循這些指導方針。  
  
- 命令可以放置群組中僅限、 群組只能置於功能表和功能表可以放置只在群組中。 只有功能表會實際顯示在 IDE 中，群組和命令不是。  
  
- 子功能表不能直接指派至 功能表中，但必須指派給群組，依序指派給一個功能表。  
  
- 命令、 子功能表和群組，都可以指派給一個父群組或使用其定義的指示詞的父欄位的功能表。  
  
- 組織只會透過指示詞中的父欄位的命令資料表有相當大的限制。 定義物件的指示詞可以採用只有一個父引數。  
  
- 重複使用的命令、 群組或子功能表需要使用新的指示詞，以建立物件的新執行個體有其專屬`GUID:ID`組。  
  
- 每個`GUID:ID`組必須是唯一的。 重複使用的命令，例如放在功能表上，工具列，或在內容功能表上，由<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>介面。  
  
- 命令和子功能表也可以指派多個群組，並使用多個功能表指派給群組[Commands 元素](../../extensibility/commands-element.md)。  
  
## <a name="vsct-file-notes"></a>.Vsct 檔案資訊  
 如果同時進行編譯並將它放在原生的附屬 DLL 之後，您可以進行.vsct 檔的任何變更，您應該執行**devenv.exe /setup /nosetupvstemplates**。 執行此動作會強制在實驗性的登錄，以可重新讀取及描述的內部資料庫中指定的 VSPackage 資源[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]重建。  
  
 在開發期間，可能會建立並註冊在實驗登錄區可能會導致令人困惑的雜亂，在 IDE 中的多個 VSPackage 專案。 若要修正此問題，您可以將實驗登錄區重設的預設設定值，來移除所有已註冊的 Vspackage 和可能的 ide 所做的變更。 若要重設實驗登錄區，請使用 CreateExpInstance.exe 工具隨附於 Visual Studio SDK。 您可以找到在  
  
 **%PROGRAMFILES(x86)%\Visual Studio \<version> SDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe**  
  
 使用命令列執行此工具**CreateExpInstance /Reset**。 請記住，此工具會移除從實驗登錄區通常不會安裝使用的所有已註冊的 Vspackage [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]。  
  
## <a name="see-also"></a>另請參閱  
 [擴充功能表和命令](../../extensibility/extending-menus-and-commands.md)

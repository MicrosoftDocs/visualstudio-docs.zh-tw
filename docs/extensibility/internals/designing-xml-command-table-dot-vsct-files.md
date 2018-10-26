---
title: 設計 XML 命令資料表 (。Vsct) 檔案 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, designing
ms.assetid: bb87a322-bac4-4258-92bc-9a876f05d653
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4e94d93d407f7499afbd43c8af2b7532ca1b4d8e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49934557"
---
# <a name="design-xml-command-table-vsct-files"></a>設計 XML 命令表檔案 (.vsct)
XML 命令資料表 (*.vsct*) 檔案描述的版面配置和外觀 VSPackage 的命令項目。 命令的項目包括按鈕、 下拉式方塊、 功能表、 工具列和命令項目的群組。 本文說明 XML 命令表檔案、 它們如何影響命令的項目和功能表，以及如何加以建立。

## <a name="commands-menus-groups-and-the-vsct-file"></a>命令、 功能表、 群組和.vsct 檔
 *.Vsct*周圍命令、 功能表和命令群組來組織檔案。 在 XML 標記 *.vsct*檔案的代表每個項目，以及其他相關聯的項目，例如命令按鈕、 命令位置與點陣圖。

 當您執行建立新的 VSPackage[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]封裝範本，範本會產生 *.vsct*檔案的必要項目 功能表命令、 工具視窗中，或自訂編輯器中，視您的選擇而定。 這 *.vsct*檔再經過修改以符合特定 VSPackage 的需求。 如需如何修改的範例 *.vsct*檔案，請參閱[擴充功能表和命令](../../extensibility/extending-menus-and-commands.md)。

 若要建立新的、 空白 *.vsct*檔案，請參閱[如何： 建立 *.vsct*檔案](../../extensibility/internals/how-to-create-a-dot-vsct-file.md)。 建立之後，您加入 XML 項目、 屬性和值來描述命令項目配置的檔案。 詳細的 XML 結構描述，請參閱 < [VSCT XML 結構描述參考](../../extensibility/vsct-xml-schema-reference.md)。

## <a name="differences-between-ctc-and-vsct-files"></a>.Ctc 和.vsct 檔之間的差異
 雖然在標記的 XML 背後的意義 *.vsct*檔案會與這些標記中現在已被取代相同 *.ctc*檔案格式，其實作會有點不同：

- 新 **\<extern >** 標記是您參考其他 *.h*檔案進行編譯，例如那些檔案進行[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]工具列。

- 雖然 *.vsct*檔案支援 **/include**陳述式，作為 *.ctc*檔案，也提供新**\<匯入 >** 項目。 差異在於， **/include**帶入*所有*的資訊，而**\<匯入 >** 帶入只有名稱。

- 雖然 *.ctc*檔案需要您在其中定義您的前置處理器指示詞的標頭檔，並不需要 *.vsct*檔案。 相反地，將您的指示詞放在符號表中，位於**\<符號 >** 項目，位於底部 *.vsct*檔案。

- *.vsct*檔案的功能**\<註釋 >** 標記，可讓您內嵌任何您喜歡，例如資訊或甚至是圖片的資訊。

- 值會儲存為項目上的屬性。

- 可以儲存個別或堆疊命令旗標。  IntelliSense，不過，不適用於堆疊的命令旗標。 如需有關命令旗標的詳細資訊，請參閱[CommandFlag 元素](../../extensibility/command-flag-element.md)。

- 您可以指定多個類型，例如分割下拉式清單、 combos 等等。

- 未驗證的 Guid。

- 每個 UI 項目具有與它所顯示的文字表示的字串。

- 父代是選擇性的。 如果省略，該值*未知群組*用。

- *圖示*引數是選擇性。

- 點陣圖區段： 此區段是相同 *.ctc*檔案中，不同之處在於您現在可以指定檔案名稱，透過將所要提取的 Href *vsct.exe*編譯器在編譯時期。

- ResID： 舊點陣圖的資源識別碼可使用還在運作中的相同 *.ctc*檔案。

- HRef： 新方法，可讓您指定點陣圖資源的檔案名稱。 它會假設所有會使用，因此您可以略過使用的區段。 編譯器會先搜尋檔案，則任何網路共用上的本機資源和所定義的任何資源 **/I**切換。

- 您不再需要按鍵繫結關係： 指定模擬器。 如果您指定其中一個，編譯器會假設編輯器和模擬器都相同。

- Keychord: Keychord 已經卸除。 新的格式是*Key1、 Mod1、 Key2、 Mod2*。  您可以指定字元、 十六進位或 VK 常數。
       
新的編譯器中， *vsct.exe*，會同時編譯 *.ctc*並 *.vsct*檔案。 舊*ctc.exe*不過，編譯器會無法辨識或編譯 *.vsct*檔案。

您可以使用*vsct.exe*編譯器来轉換的現有 *.cto*檔案載入 *.vsct*檔案。 如需詳細資訊，請參閱 <<c0> [ 如何： 從現有的.cto 檔建立.vsct 檔](../../extensibility/internals/how-to-create-a-dot-vsct-file.md#how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file)。

## <a name="the-vsct-file-elements"></a>.Vsct 檔項目
 命令資料表具有下列階層和項目：

 [CommandTable 元素](../../extensibility/commandtable-element.md)： 代表所有的命令、 功能表群組和 VSPackage 相關聯的功能表。

 [Extern 元素](../../extensibility/extern-element.md)： 參考任何您想要合併的外部的.h 檔案 *.vsct*檔案。

 [包含項目](../../extensibility/include-element.md)： 您想要編譯連同任何其他標頭 (.h) 檔案會參考您 *.vsct*檔案。 A *.vsct*檔案可以包含 *.h*檔案包含定義命令、 功能表群組和功能表的 IDE 或另一個 VSPackage 提供的常數。

 [Commands 元素](../../extensibility/commands-element.md)： 代表所有可執行的個別命令。 每個命令有下列 4 個子元素：

 [功能表項目](../../extensibility/menus-element.md)： 代表所有的功能表和工具列在 VSPackage 中的。 功能表是容器群組的命令。

 [Groups 元素](../../extensibility/groups-element.md)： 代表所有在 VSPackage 中的群組。 群組為個別命令的集合。

 [Buttons 元素](../../extensibility/buttons-element.md)： 代表所有的命令按鈕和功能表項目，在 VSPackage 中的。 按鈕是可以與命令相關聯的視覺控制項。

 [Bitmaps 元素](../../extensibility/bitmaps-element.md)： 代表所有針對所有的按鈕，在 VSPackage 中的點陣圖。 點陣圖是顯示旁，或在 [命令] 按鈕，視內容而定的圖片。

 [CommandPlacements 元素](../../extensibility/commandplacements-element.md)： 指出其中應設置個別的命令功能表的 VSPackage 中的其他位置。

 [VisibilityConstraints 元素](../../extensibility/visibilityconstraints-element.md)： 指定是否命令完全顯示時間，或只在特定內容中，例如特定的對話方塊或視窗會顯示。 功能表和命令的值，這個項目會顯示指定的內容為作用中時，才。 預設行為是以隨時顯示命令。

 [KeyBindings 元素](../../extensibility/keybindings-element.md)： 指定命令的任何索引鍵繫結。 也就是一或多個按鍵組合，必須執行的命令，例如按下**Ctrl**+**S**。

 [UsedCommands 元素](../../extensibility/usedcommands-element.md)： 通知[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]環境雖然指定的命令由其他程式碼中，實作，使用目前的 VSPackage 時，它會提供命令的實作。

 [Symbols 元素](../../extensibility/symbols-element.md)： 包含的符號名稱和 GUID 識別碼，所有您在封裝中的命令。

## <a name="vsct-file-design-guidelines"></a>.vsct 檔的設計指導方針
 已成功設計 *.vsct*檔案，請遵循下列指導方針。

-   命令可以放置群組中僅限、 群組只能置於功能表和功能表可以放置只在群組中。 只有功能表會實際顯示在 IDE 中，群組和命令不是。

-   子功能表不能直接指派至 功能表中，但必須指派給群組，依序指派給一個功能表。

-   命令的子功能表和群組，都可以指派給一個父群組或使用其定義的指示詞的父欄位的功能表。

-   組織只會透過指示詞中的父欄位的命令資料表有相當大的限制。 定義物件的指示詞可以採用只有一個父引數。

-   重複使用的命令、 群組或子功能表需要使用新的指示詞，以建立物件的新執行個體有其專屬`GUID:ID`組。

-   每個`GUID:ID`組必須是唯一的。 重複使用的命令，例如放在功能表上，工具列，或在內容功能表上，由<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>介面。

-   命令和子功能表也可以指派多個群組，並使用多個功能表指派給群組[Commands 元素](../../extensibility/commands-element.md)。

## <a name="vsct-file-notes"></a>.vsct 檔案資訊
 如果您進行任何變更 *.vsct*檔案您同時進行編譯，並且將它放在原生的附屬 DLL 之後，您應該執行**devenv.exe /setup /nosetupvstemplates**。 執行是強制的實驗性的登錄，以可重新讀取和描述的內部資料庫中指定的 VSPackage 資源[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]重建。

 在開發期間，可能會建立並註冊在實驗登錄區可能會導致令人困惑的雜亂，在 IDE 中的多個 VSPackage 專案。 若要修正此問題，您可以將實驗登錄區重設的預設設定值，來移除所有已註冊的 Vspackage 和可能的 ide 所做的變更。 若要重設實驗登錄區，請使用 CreateExpInstance.exe 工具隨附於 Visual Studio SDK。 您可以找到在：

 *%Programfiles (x86) %\Visual Studio\\\<版本 > SDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe*

 使用命令來執行此工具**CreateExpInstance /Reset**。 請記住，此工具會移除從實驗登錄區通常不會安裝使用的所有已註冊的 Vspackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。

## <a name="see-also"></a>另請參閱
 [擴充功能表和命令](../../extensibility/extending-menus-and-commands.md)
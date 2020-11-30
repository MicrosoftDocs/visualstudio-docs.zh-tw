---
title: 設計 XML 命令表 (。.Vsct) Files |Microsoft Docs
description: 瞭解如何設計 XML 命令表 ( .vsct) 檔案，該檔案描述命令專案的版面配置和外觀，包括按鈕、下拉式方塊、功能表和工具列。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, designing
ms.assetid: bb87a322-bac4-4258-92bc-9a876f05d653
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a1ccab1eddf38e2f93cb00f1f5fdea6ce09f2f05
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/30/2020
ms.locfileid: "96328427"
---
# <a name="design-xml-command-table-vsct-files"></a>設計 XML 命令表 ( .vsct) 檔案
XML 命令表 (*.vsct*) 檔描述 VSPackage 的命令專案的配置和外觀。 命令專案包括按鈕、下拉式方塊、功能表、工具列和命令專案群組。 本文說明 XML 命令表格檔案、它們如何影響命令專案和功能表，以及如何建立它們。

## <a name="commands-menus-groups-and-the-vsct-file"></a>命令、功能表、群組和 .vsct 檔案
 *.Vsct* 檔案會以命令、功能表和命令群組來組織。 *.Vsct* 檔案中的 XML 標記代表每一個專案，以及其他相關聯的專案，例如命令按鈕、命令位置和點陣圖。

 當您藉由執行套件範本來建立新的 VSPackage 時 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ，範本會根據您的選取專案，使用功能表命令、工具視窗或自訂編輯器的必要元素來產生 *.vsct 檔案。* 然後您可以修改這個 *.vsct* 檔案，以符合特定 VSPackage 的需求。 如需如何修改 *.vsct* 檔的範例，請參閱 [擴充功能表和命令](../../extensibility/extending-menus-and-commands.md)。

 若要建立新的空白 *.vsct* 檔案，請參閱 [如何：建立 *.vsct*](../../extensibility/internals/how-to-create-a-dot-vsct-file.md)檔案。 一旦建立之後，您可以將 XML 元素、屬性和值加入至檔案，以描述命令專案配置。 如需詳細的 XML 架構，請參閱 [.VSCT xml 架構參考](../../extensibility/vsct-xml-schema-reference.md)。

## <a name="differences-between-ctc-and-vsct-files"></a>.Ctc 和. .vsct 檔案之間的差異
 雖然 *.vsct* 檔中的 XML 標記背後的意義與 *.ctc* 檔案格式的標記相同，但其執行方式有點不同：

- 新 **\<extern>** 標記是您參考其他 *.h* 檔案的位置，例如工具列的檔案 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。

- *.Vsct* 檔案支援 **/include** 語句，如同 *.ctc* 檔一樣，它也會提供新的 **\<import>** 元素功能。 差別在於， **/include** 會帶入 *所有* 資訊，而只會提供 **\<import>** 名稱。

- *.Ctc* 檔案需要您定義預處理器指示詞的標頭檔，而 *.vsct* 檔案則不需要。 相反地，請將您的指示詞放在位於 .vsct 檔案底部的元素中的符號表中 **\<Symbol>** 。 *.vsct*

- *.vsct* 檔案是一個 **\<Annotation>** 標記，可讓您內嵌任何您想要的資訊，例如便箋或甚至是圖片。

- 值會儲存為專案上的屬性。

- 您可以個別或堆疊地儲存命令旗標。  不過，IntelliSense 在堆疊的命令旗標上無法運作。 如需命令旗標的詳細資訊，請參閱 [CommandFlag 元素](../../extensibility/command-flag-element.md)。

- 您可以指定多個類型，例如分割下拉清單、combos 等。

- Guid 不會驗證。

- 每個 UI 元素都有一個字串，代表顯示的文字。

- 父系是選擇性的。 如果省略，則會使用「未知的值 *群組* 」。

- *Icon* 引數是選擇性的。

- Bitmap 區段：此區段與 *.ctc* 檔案中的相同，不同之處在于您現在可以透過 Href 指定檔案名，以在編譯時期由 *vsct.exe* 編譯器提取。

- ResID：舊的點陣圖資源識別碼可以使用，而且仍可與 *.ctc* 檔案相同。

- HRef：新的方法，可讓您為點陣圖資源指定檔案名。 它會假設全部都已使用，因此您可以省略使用的區段。 編譯器會先搜尋檔案的本機資源，然後在任何 net 共用上搜尋任何由 **/i** 參數定義的資源。

- Keybinding：您不再需要指定模擬器。 如果您指定一個，則編譯器會假設編輯器和模擬器相同。

- Keychord： Keychord 已卸載。 新的格式為 *Key1、Mod1、Key2、Mod2*。  您可以指定字元、十六進位或 VK 常數。

新的編譯器 *vsct.exe* 會編譯 *.ctc* 和 *.vsct* 檔案。 不過，舊的 *ctc.exe* 編譯器將無法辨識或編譯 *.vsct* 檔。

您可以使用 *vsct.exe* 編譯器，將現有的 *cto* 檔案轉換成 *.vsct* 檔案。 如需詳細資訊，請參閱 [如何：從現有的 cto 檔建立 .vsct](../../extensibility/internals/how-to-create-a-dot-vsct-file.md#how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file)檔。

## <a name="the-vsct-file-elements"></a>.Vsct 檔案元素
 命令資料表具有下列階層和元素：

- [CommandTable 元素](../../extensibility/commandtable-element.md)：代表與 VSPackage 相關聯的所有命令、功能表群組和功能表。

- [Extern 元素](../../extensibility/extern-element.md)：參考任何您想要與 *.vsct* 檔案合併的外部 .h 檔案。

- [Include 元素](../../extensibility/include-element.md)：參考您要與 *.vsct* 檔案一起編譯的任何額外標頭 ( .h) 檔案。 *.Vsct* 檔案可以包含包含常數的 *.h* 檔案，以定義 IDE 或其他 VSPackage 提供的命令、功能表群組和功能表。

- [命令元素](../../extensibility/commands-element.md)：代表可以執行的所有個別命令。 每個命令都有下列四個子項目：

- Menu[元素](../../extensibility/menus-element.md)：代表 VSPackage 中的所有功能表和工具列。 功能表是命令群組的容器。

- [Groups 元素](../../extensibility/groups-element.md)：代表 VSPackage 中的所有群組。 群組是個別命令的集合。

- [按鈕元素](../../extensibility/buttons-element.md)：代表 VSPackage 中的所有命令按鈕和功能表項目。 按鈕是可以與命令相關聯的視覺控制項。

- [點陣圖元素](../../extensibility/bitmaps-element.md)：代表 VSPackage 中所有按鈕的所有點陣圖。 點陣圖是在命令按鈕旁邊顯示的圖片，視內容而定。

- [CommandPlacements 元素](../../extensibility/commandplacements-element.md)：表示個別命令應放置在 VSPackage 功能表中的其他位置。

- [VisibilityConstraints 元素](../../extensibility/visibilityconstraints-element.md)：指定命令是否會在任何時間顯示，或只顯示在特定的內容中，例如當特定對話方塊或視窗顯示時。 只有當指定的內容為作用中時，才會顯示具有這個元素值的功能表和命令。 預設行為是隨時顯示命令。

- [Keybindings.json 元素](../../extensibility/keybindings-element.md)：指定命令的任何按鍵系結。 也就是說，必須按下一或多個按鍵組合，才能執行命令，例如 **Ctrl** + **S**。

- [UsedCommands 元素](../../extensibility/usedcommands-element.md)：告知 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 環境，雖然指定的命令是由其他程式碼執行，但當目前的 VSPackage 為使用中時，它會提供命令執行。

- [符號元素](../../extensibility/symbols-element.md)：包含封裝中所有命令的符號名稱和 GUID 識別碼。

## <a name="vsct-file-design-guidelines"></a>.vsct 檔案設計指導方針
 若要成功設計 *.vsct* 檔，請遵循這些指導方針。

- 命令只能放在群組中，群組只能放在功能表中，而且只能在群組中放入功能表。 IDE 中只會顯示功能表，不會實際顯示群組和命令。

- 子功能表無法直接指派給功能表，但必須指派給群組，然後再指派給功能表。

- 您可以使用其定義指示詞的父欄位，將命令、子功能表和群組指派給一個父群組或功能表。

- 只透過指示詞中的父欄位來組織命令資料表有很大的限制。 定義物件的指示詞只能採用一個父引數。

- 重複使用命令、群組或子功能表時，必須使用新的指示詞，以它自己的配對來建立物件的新實例 `GUID:ID` 。

- 每個 `GUID:ID` 配對都必須是唯一的。 例如，重複使用已放在功能表、工具列或內容功能表上的命令，會由 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 介面處理。

- 您也可以將命令和子功能表指派給多個群組，並使用 [ [命令] 元素](../../extensibility/commands-element.md)將群組指派給多個功能表。

## <a name="vsct-file-notes"></a>.vsct 檔案注意事項
 如果您在編譯後對 *.vsct* 檔案進行任何變更，並將它放在原生附屬 DLL 中，則應該執行 **devenv.exe/setup/nosetupvstemplates**。 這麼做會強制將實驗登錄中指定的 VSPackage 資源重新讀取，以及描述要重建的內部資料庫 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。

 在開發期間，有可能會在實驗登錄區中建立並註冊多個 VSPackage 專案，這可能會導致 IDE 中的雜亂混淆。 若要修正此問題，您可以將實驗性 hive 重設為預設值，以移除所有已註冊的 Vspackage 以及它們可能對 IDE 進行的任何變更。 若要重設實驗性 hive，請使用 Visual Studio SDK 隨附的 CreateExpInstance.exe 工具。 您可以在下列位置找到：

 *% PROGRAMFILES (x86) % \ Visual Studio \\ \<version> SDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe*

 使用命令 **CreateExpInstance/Reset** 來執行工具。 請記住，此工具會從實驗性 hive 中移除所有未隨一般安裝的已註冊 Vspackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。

## <a name="see-also"></a>另請參閱
- [擴充功能表和命令](../../extensibility/extending-menus-and-commands.md)

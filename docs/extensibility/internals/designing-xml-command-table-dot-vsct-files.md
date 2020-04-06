---
title: 設計 XML 指令表 (.Vsct) 檔案 :微軟文件
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
ms.openlocfilehash: fcd29aee98139bb151c87590b256df6b8370abff
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708745"
---
# <a name="design-xml-command-table-vsct-files"></a>設計 XML 指令表 (.vsct) 檔案
XML 命令表 *(.vsct*) 檔案描述 VSPackage 的命令項的佈局和外觀。 命令項包括按鈕、組合框、功能表、工具列和命令項組。 本文介紹了 XML 命令表檔、它們如何影響命令項和功能表以及如何創建它們。

## <a name="commands-menus-groups-and-the-vsct-file"></a>指令、選單、群組和 .vsct 檔案
 *.vsct*文件圍繞命令、功能表和命令組進行組織。 *.vsct*檔中的 XML 標籤表示每個項,以及其他關聯的項,如命令按鈕、命令放置和位圖。

 通過運行[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]包範本建立新的 VSPackage 時,樣本會生成一個 *.vsct*檔,該檔包含功能表命令、工具視窗或自訂編輯器的必要元素,具體取決於您的選擇。 然後可以修改此 *.vsct*檔案以滿足特定 VSPackage 的要求。 有關如何修改 *.vsct*檔案的範例,請參閱[延伸選單和指令](../../extensibility/extending-menus-and-commands.md)。

 要建立新的空白 *.vsct*檔案,請參考[如何:建立 *.vsct*檔案](../../extensibility/internals/how-to-create-a-dot-vsct-file.md)。 建立後,向檔添加 XML 元素、屬性和值以描述命令項佈局。 有關詳細的 XML 架構,請參考[VSCT XML 架構參考](../../extensibility/vsct-xml-schema-reference.md)。

## <a name="differences-between-ctc-and-vsct-files"></a>.ctc 和 .vsct 檔案之間的差異
 雖然 *.vsct*檔中的 XML 標記背後的含義與現在棄用*的 .ctc*檔格式中的這些標記相同,但它們的實現卻略有不同:

- 新的**\<extern>** 標記是參考要編譯的其他 *.h*檔的位置,[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]例如工具列的檔案 。

- 雖然 *.vsct*檔案支援 **/include**語句,就像 *.ctc*檔一樣,但它也具有新的**\<導入>** 元素。 區別在於 **/包括**帶來了*所有*資訊,而**\<導入>** 只帶來名稱。

- 雖然 *.ctc*檔需要一個頭檔,您可以在其中定義預處理器指令,*但 .vsct*檔不需要一個。 相反,將指令放在符號表中,該表位於位於 *.vsct*檔底部的**\<符號>** 元素中。

- *.vsct*檔具有**\<註釋>** 標記,允許您嵌入任何你喜歡的資訊,如筆記,甚至圖片。

- 值存儲為項上的屬性。

- 命令標誌可以單獨存儲或堆疊。  但是,IntelliSense 不適用於堆疊的命令標誌。 有關命令旗標的詳細資訊,請參考[指令Flag元素](../../extensibility/command-flag-element.md)。

- 您可以指定多種類型,如拆分下拉、組合等。

- GUID 不驗證。

- 每個 UI 元素都有一個字串,表示與它一起顯示的文本。

- 父級是可選的。 如果省略,則使用值*組"未知*"。

- *圖示*參數是可選的。

- Bitmap 部分:此部分與 *.ctc*檔中相同,只不過您現在可以通過 href指定檔名,該檔名將在編譯時由*vsct.exe*編譯器拉取。

- ResID:可以使用舊的位圖資源 ID,並且仍然與 *.ctc*檔中的工作方式相同。

- HRef:一種新方法,允許您為位圖資源指定檔名。 它假定所有都已使用,因此您可以省略"已使用"部分。 編譯器將首先搜索檔的本地資源,然後在任何網路共用上搜索 **/I**開關定義的任何資源。

- 金鑰綁定:您不再需要指定模擬器。 如果指定了一個,編譯器將假定編輯器和模擬器相同。

- 基喬德:基喬德已經掉了下來。 新格式為*Key1、Mod1、Key2、Mod2*。  您可以指定字元、十六進位或 VK 常量。

新的編譯器 *,vsct.exe,* 編譯 *.ctc*和 *.vsct*檔。 但是,舊的*ctc.exe*編譯器不會識別或編譯 *.vsct*檔。

您可以使用*vsct.exe*編譯器將現有的 *.cto*檔案轉換為 *.vsct*檔案。 關於詳細資訊,請參閱[如何:從現有的 .cto 檔案建立 .vsct 檔案](../../extensibility/internals/how-to-create-a-dot-vsct-file.md#how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file)。

## <a name="the-vsct-file-elements"></a>.vsct 檔案元素
 指令表具有以下層次結構和元素:

- [命令表元素](../../extensibility/commandtable-element.md):表示與 VSPackage 關聯的所有命令、功能表組和功能表。

- [Extern 元素](../../extensibility/extern-element.md):引用要與 *.vsct*檔案合併的任何外部 .h 檔。

- [包括元素](../../extensibility/include-element.md):引用要與 *.vsct*檔一起編譯的任何其他標頭 (.h) 檔。 *.vsct*檔案可以包含包含定義 IDE 或其他 VSPackage 提供的命令、功能表組和選單的常量的 *.h*檔。

- [命令元素](../../extensibility/commands-element.md):表示可以執行的所有單個命令。 每個指令具有以下四個子元素:

- [選單元素](../../extensibility/menus-element.md):表示 VSPackage 中的所有功能表和工具列。 選單是命令組的容器。

- [組元素](../../extensibility/groups-element.md):表示 VS 包中的所有組。 組是單個命令的集合。

- [按鈕元素](../../extensibility/buttons-element.md):表示 VSPackage 中的所有命令按鈕和功能表項。 按鈕是可與命令關聯的可視控件。

- [點陣圖元素](../../extensibility/bitmaps-element.md):表示 VSPackage 中所有按鈕的所有位圖。 位貼圖是顯示在命令按鈕旁邊或上陣的圖片,具體取決於上下文。

- [命令放置元素](../../extensibility/commandplacements-element.md):指示應在 VSPackage 功能表中放置各個命令的其他位置。

- [可見性約束元素](../../extensibility/visibilityconstraints-element.md):指定命令是否在所有時間顯示,或僅在某些上下文中(例如顯示特定對話框或視窗時)顯示。 只有指定上下文處於活動狀態時,才顯示具有此元素值的功能表和命令。 默認行為是隨時顯示該命令。

- [鍵綁定元素](../../extensibility/keybindings-element.md):指定命令的任何鍵綁定。 也就是說,必須按下一個或多個鍵組合才能執行命令,如**Ctrl**+**S**。

- [已用命令元素](../../extensibility/usedcommands-element.md):[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]通知 環境,儘管指定的命令由其他代碼實現,但當當前 VSPackage 處於活動狀態時,它提供命令實現。

- [符號元素](../../extensibility/symbols-element.md):包含包中所有命令的符號名稱和 GUID ID。

## <a name="vsct-file-design-guidelines"></a>.vsct 檔案設計指南
 要成功設計 *.vsct*檔,請遵循以下準則。

- 命令只能放在組中,組只能放置在菜單中,功能表只能放在組中。 實際上只有菜單顯示在 IDE 中,組和命令不顯示。

- 子功能表不能直接分配給菜單,但必須分配給組,而組又分配給菜單。

- 可以使用命令、子功能表和組的定義指令的父欄位將命令、子功能表和組分配給一個育兒組或功能表。

- 僅通過指令中的父欄段組織命令表存在很大限制。 定義物件的指令只能採用一個父參數。

- 重用命令、組或子功能表需要使用新指令創建具有其自身`GUID:ID`對的物件的新實例。

- 每`GUID:ID`對必須是唯一的。 重複使用一個命令,例如,已放置在功能表,工具列,或上下文菜單,由<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>介面處理。

- 命令和子功能表也可以分配給多個組,並且可以使用[命令元素](../../extensibility/commands-element.md)將組分配給多個功能表。

## <a name="vsct-file-notes"></a>.vsct 檔案註解
 如果在編譯 *.vsct*檔並將其放在本機衛星 DLL 中後對其進行任何更改,則應執行**devenv.exe /setup /nosetupvstemplates**。 這樣做將強制重新讀取實驗註冊表中指定的 VSPackage 資源以及[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]描述 要重建的內部資料庫。

 在開發過程中,可以在實驗註冊表配置單元中創建和註冊多個 VSPackage 專案,這可能導致 IDE 中的混亂混亂。 要解決此問題,您可以將實驗配置單元重置為預設設置,以刪除所有已註冊的 VS 包以及它們可能對 IDE 所做的任何更改。 要重置實驗配置單元,請使用 Visual Studio SDK 附帶的 CreateExpInstance.exe 工具。 您可以在:

 *%PROGRAMFILES(x86)%\視覺工作室\\\<版本> SDK_VisualStudio 整合\工具\Bin_createExpInstance.exe*

 使用命令**CreateExp 實例 /重置**執行該工具。 請記住,此工具從實驗配置單元中刪除通常不安裝[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]的所有已註冊的 VS 包。

## <a name="see-also"></a>另請參閱
- [延伸選單與指令](../../extensibility/extending-menus-and-commands.md)

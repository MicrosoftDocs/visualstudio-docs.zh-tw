---
title: 深入探索編輯器
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - architecture
ms.assetid: 822cbb8d-7ab4-40ee-bd12-44016ebcce81
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bba0b5192df53b6ec837b0030c7b236bf8e08dea
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710319"
---
# <a name="inside-the-editor"></a>編輯器內部

編輯器由幾個不同的子系統組成,這些子系統旨在使編輯器文本模型與文本視圖和用戶介面分開。

這些部份描述了編輯器的不同方面:

- [子系統概述](../extensibility/inside-the-editor.md#overview-of-the-subsystems)

- [文字模型](../extensibility/inside-the-editor.md#the-text-model)

- [文字檢視](../extensibility/inside-the-editor.md#the-text-view)

這些部份描述編輯器的功能:

- [標記與分類器](../extensibility/inside-the-editor.md#tags-and-classifiers)

- [裝飾品](../extensibility/inside-the-editor.md#adornments)

- [投影](../extensibility/inside-the-editor.md#projection)

- [大綱](../extensibility/inside-the-editor.md#outlining)

- [滑鼠結合](../extensibility/inside-the-editor.md#mouse-bindings)

- [編輯器操作](../extensibility/inside-the-editor.md#editor-operations)

- [IntelliSense](../extensibility/inside-the-editor.md#intellisense)

## <a name="overview-of-the-subsystems"></a>子系統概述

### <a name="text-model-subsystem"></a>文字模型子系統

文字模型子系統負責表示文本並啟用其操作。 文字模型子系統包含<xref:Microsoft.VisualStudio.Text.ITextBuffer>介面,該介面描述編輯器要顯示的字元序列。 可以通過多種方式修改、跟蹤或以其他方式操作此文本。 文字模型還提供以下方面的類型:

- 將文字與檔案關聯,並在檔案系統中管理讀取和寫入這些文件的服務。

- 一種不同的服務,它查找兩個物件序列之間的最小差異。

- 一種系統,用於根據其他緩衝區中文本的子集在緩衝區中描述文本。

文本模型子系統沒有用戶介面 (UI) 概念。 例如,它不負責文本格式或文本佈局,並且不瞭解可能與文本關聯的可視修飾。

文本模型子系統的公共類型包含在*Microsoft.VisualStudio.Text.Data.dll*和*Microsoft.VisualStudio.CoreUtility.dll 中*,它們僅依賴於 .NET 框架基類庫和託管擴展性框架 (MEF)。

### <a name="text-view-subsystem"></a>文字檢視系統

文字檢視子系統負責設定文本的格式和顯示。 此子系統中的類型分為兩層,具體取決於類型是否依賴於 Windows 演示文稿基礎 (WPF)。 最重要的類型是<xref:Microsoft.VisualStudio.Text.Editor.ITextView><xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>和 ,它控制要顯示的文本列集,以及使用 WPF UI 元素進行修飾文本的加註、選擇和修飾文本的設施。 此子系統還提供文本顯示區域周圍的邊距。 這些邊距可以擴展,並可以包含不同類型的內容和視覺效果。 邊距的範例包括行號顯示和滾動條。

文字檢視系統的公共類型包含在*Microsoft.VisualStudio.Text.UI.dll*和*Microsoft.VisualStudio.Text.UI.Wpf.dll 中*。 第一個程式集包含與平台無關的元素,第二個程式集包含特定於 WPF 的元素。

### <a name="classification-subsystem"></a>類別子系統

分類子系統負責確定文本的字體屬性。 分類器將文本分成不同的類,例如"關鍵字"或"註釋"。 分類格式映射將這些類與實際字體屬性相關聯,例如"藍色 Consolas 10 pt"。 文字檢視在設定文字格式和呈現文本時使用此資訊。 在本主題的後面部分介紹的標記使數據能夠與文本範圍相關聯。

分類子系統的公共類型包含在 Microsoft.VisualStudio.Text.Logic.dll 中,它們與 Microsoft.VisualStudio.Text.UI.Wpf.dll 中包含的分類的可視方面進行交互。

### <a name="operations-subsystem"></a>作業子系統

操作子系統定義編輯器行為。 它為 Visual Studio 編輯器命令和撤銷系統提供了實現。

## <a name="a-closer-look-at-the-text-model-and-the-text-view"></a>仔細檢視文字模型和文字檢視

### <a name="the-text-model"></a>文字模型

文本模型子系統由不同的文本類型分組組成。 其中包括文本緩衝區、文本快照和文本範圍。

#### <a name="text-buffers-and-text-snapshots"></a>文字緩衝區與文字快照

該<xref:Microsoft.VisualStudio.Text.ITextBuffer>介面表示使用 UTF-16 編碼的 Unicode 字元序列,UTF-16 是`String`.NET 框架中的類型使用的編碼。 文本緩衝區可以保留為文件系統文檔,但這不是必填項。

<xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>用於創建空文本緩衝區或從字串或 初始<xref:System.IO.TextReader>化的文本緩衝區。 文字緩衝區可以作為 儲存到檔案<xref:Microsoft.VisualStudio.Text.ITextDocument>系統 。

任何線程都可以編輯文本緩衝區,直到線程通過調用<xref:Microsoft.VisualStudio.Text.ITextBuffer.TakeThreadOwnership%2A>獲取文本緩衝區的擁有權。 之後,只有該線程可以執行編輯。

文本緩衝區在其生存期內可以遍遍多個版本。 每次編輯緩衝區時都會生成新版本,並且不可變<xref:Microsoft.VisualStudio.Text.ITextSnapshot>表示該緩衝區版本的內容。 由於文本快照是不可變的,因此即使文本快照繼續更改,也可以不受限制地訪問任何線程上的文本快照。

#### <a name="text-snapshots-and-text-snapshot-lines"></a>文字快照與文字快照行

您可以將文字快照的內容視為字元序列或列序列。 字元和行都從零開始編製索引。 空文本快照包含零個字元和一行空行。 行由任何有效的 Unicode 換行字元序列或緩衝區的開頭或結尾分隔。 換行符在文字快照中顯式表示,文本快照中的換行符不一定全部相同。

> [!NOTE]
> 有關 Visual Studio 編輯器中換行符號的詳細資訊,請參考[編碼與換行](../ide/encodings-and-line-breaks.md)符號 。

文本行由物件<xref:Microsoft.VisualStudio.Text.ITextSnapshotLine>表示,可以從特定行號或特定字元位置的文本快照獲取該物件。

#### <a name="snapshotpoints-snapshotspans-and-normalizedsnapshotspancollections"></a>快照點、快照範圍和規範化快照跨集合

表示<xref:Microsoft.VisualStudio.Text.SnapshotPoint>快照中的字元位置。 該位置保證位於零和快照長度之間。 表示<xref:Microsoft.VisualStudio.Text.SnapshotSpan>快照中的文本範圍。 其結束位置保證位於零和快照長度之間。 由<xref:Microsoft.VisualStudio.Text.NormalizedSnapshotSpanCollection>同一快照<xref:Microsoft.VisualStudio.Text.SnapshotSpan>中的一組對象組成。

#### <a name="spans-and-normalizedspancollections"></a>跨和標準化跨值集合

表示<xref:Microsoft.VisualStudio.Text.Span>可應用於文本快照中的文本範圍的間隔。 快照位置是零基的,因此範圍可以從任何位置開始,包括零。 範圍`End`的屬性等於其`Start`屬性`Length`及其 屬性的總和。 `Span`不包括由 屬性索引`End`的字元。 例如,具有 Start=5 和 Length=3 的跨距具有 End=8,並且它包括位置 5、6 和 7 處的字元。 此跨度的表示法為 [5...8)。

如果兩個跨段具有任何共同位置(包括結束位置),則它們相交。 因此,[3, 5) 和 #2, 7) 的交點為 [3, 5) 和 [5, 7) 的交點為 [5, 5)。 (請注意,[5, 5) 是一個空跨度。

兩個跨距重疊,如果它們具有共同位置,則"結束"位置除外。 空範圍永遠不會重疊任何其他範圍,並且兩個範圍的重疊永遠不會為空。

A<xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection>是跨範圍的"開始"屬性的順序的跨範圍清單。 在清單中,重疊或對頭跨度合併。 例如,給定範圍集 [5...9"、"0..1"、"{3..6]和 [9..10),規範化範圍列表為 [0..1][3..10] 。

#### <a name="itextedit-textversion-and-text-change-notifications"></a>IText 編輯、文字版本和文字變更通知

可以使用<xref:Microsoft.VisualStudio.Text.ITextEdit>物件更改文本緩衝區的內容。 建立此類物件(透過使用`CreateEdit()`<xref:Microsoft.VisualStudio.Text.ITextBuffer>的方法之一)將啟動由文本編輯組成的文本事務。 每次編輯都會將緩衝區中的某些文本跨度由字串替換。 每次編輯的座標和內容都相對於啟動事務時緩衝區的快照表示。 物件<xref:Microsoft.VisualStudio.Text.ITextEdit>調整受同一事務中其他編輯影響的編輯的座標。

例如,請考慮包含此字串的文字緩衝區:

```
abcdefghij
```

套用包含兩個編輯的事務,一個編輯使用字`X`元 替換範圍在 {2..4),第二個編輯`Y`使用字元 替換範圍在 {6..9} 結果是此緩衝區:

```
abXefYj
```

在應用第一次編輯之前,針對事務開頭的緩衝區內容計算第二個編輯的座標。

當通過調用其<xref:Microsoft.VisualStudio.Text.ITextEdit>`Apply()`方法提交物件時,對緩衝區的更改將生效。 如果至少有一個非空編輯,則創建一個新<xref:Microsoft.VisualStudio.Text.ITextVersion>編輯,創建一個新<xref:Microsoft.VisualStudio.Text.ITextSnapshot>編輯,並引發一個`Changed`事件。 每個文字版本都有不同的文本快照。 文本快照表示編輯事務後文本緩衝區的完整狀態,但文本版本僅描述從一個快照到下一個快照的更改。 通常,文本快照要使用一次,然後丟棄,而文本版本必須保持一段時間的處於活動狀態。

文字版本包含<xref:Microsoft.VisualStudio.Text.INormalizedTextChangeCollection>。 此集合描述應用於快照時產生後續快照的更改。 集合<xref:Microsoft.VisualStudio.Text.ITextChange>中的每個成員都包含更改的字元位置、替換的字串和替換字串。 替換的字串對於基本插入為空,替換字串為空,用於基本刪除。 規範化集合始終`null`用於最新版本的文本緩衝區。

任何時候都只能<xref:Microsoft.VisualStudio.Text.ITextEdit>實例化一個物件的文本緩衝區,並且所有文本編輯都必須在擁有文本緩衝區的線程上執行(如果已聲明擁有權)。 可以通過調用`Cancel`文本 編輯的方法`Dispose`或方法 來放棄文本編輯。

<xref:Microsoft.VisualStudio.Text.ITextBuffer>還提供了`Insert()``Delete()``Replace()`<xref:Microsoft.VisualStudio.Text.ITextEdit>與介面上找到的方法類似的 方法。 調用這些具有與創建<xref:Microsoft.VisualStudio.Text.ITextEdit>物件、進行類似調用以及然後應用編輯相同的效果。

#### <a name="tracking-points-and-tracking-spans"></a>追蹤點和追蹤範圍

表示<xref:Microsoft.VisualStudio.Text.ITrackingPoint>文本緩衝區中的字元位置。 如果以導致字元位置移動的方式編輯緩衝區,則跟蹤點將隨其移動。 例如,如果跟蹤點引用緩衝區中的位置 10,並且在緩衝區的開頭插入五個字元,則跟蹤點則引用位置 15。 如果插入發生在追蹤點表示的位置,則其行為由<xref:Microsoft.VisualStudio.Text.PointTrackingMode>其決定,可以是`Positive``Negative`或 。 如果追蹤模式為正,則跟蹤點引用同一字元,該字元現在位於插入的末尾。 如果跟蹤模式為負,則跟蹤點是指原始位置的第一個插入字元。 如果刪除跟蹤點表示的位置的字元,則跟蹤點將轉移到刪除範圍後的第一個字元。 例如,如果追蹤點引用位置 5 處的字元,並且位置 3 到 6 處的字元被刪除,則跟蹤點引用位置 3 處的字元。

表示<xref:Microsoft.VisualStudio.Text.ITrackingSpan>一系列字元,而不是僅表示一個位置。 其行為由其<xref:Microsoft.VisualStudio.Text.SpanTrackingMode>決定。 如果跨距跟蹤模式為[SpanTrackingMode.Edge 包容](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgeInclusive),則追蹤範圍將增大以合併插入在其邊緣的文本。 如果跨距追蹤模式為[SpanTrackIngMode.EdgeExclusive,](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgeExclusive)則追蹤範圍不包含插入在其邊緣的文本。 但是,如果跨距跟蹤模式為[「跨跟蹤模式.Edge積極](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgePositive)」,則插入會將當前位置推向起始位置,如果跨距跟蹤模式為[「跨跟蹤模式.Edge 負」,](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgeNegative)則插入將當前位置推向末端。

您可以取得追蹤點的位置或追蹤範圍的範圍,用於它們所屬的文本緩衝區的任何快照。 跟蹤點和跟蹤範圍可以從任何線程安全地引用。

#### <a name="content-types"></a>內容類型

內容類型是定義不同類型的內容的機制。 內容類型可以是文件類型,如"文本"、"代碼"或"二進制",也可以是技術類型(如"xml"、"vb"或"c#"。)。 例如,"使用"一詞是 C# 和 Visual Basic 中的關鍵字,但在其他程式設計語言中則不是關鍵字。 因此,此關鍵字的定義將僅限於"c#"和"vb"內容類型。

內容類型用作編輯器的修飾和其他元素的篩選器。 許多編輯器功能和擴展點都是根據內容類型定義的。 例如,純文字檔、XML 檔和 Visual Basic 原始程式碼檔的文本著色是不同的。 文本緩衝區通常在創建時分配內容類型,並且可以更改文本緩衝區的內容類型。

內容類型可以從其他內容類型進行多次繼承。 <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition>允許您將多個基類型指定為給定內容類型的父類型。

開發人員可以定義自己的內容類型,並使用註冊<xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>它們。 可以使用 來定義許多編輯器功能相對於特定內容<xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>類型 。 例如,可以定義編輯器邊距、修飾和滑鼠處理程式,以便它們僅適用於顯示特定內容類型的編輯器。

### <a name="the-text-view"></a>文字檢視

模型檢視控制器 (MVC) 模式的檢視部分定義文字檢視、檢視的格式、圖形元素(如滾動條)和圖。 可視化工作室編輯器的所有表示元素都基於 WPF。

#### <a name="text-views"></a>文字檢視

該<xref:Microsoft.VisualStudio.Text.Editor.ITextView>介面是文本視圖與平台無關的表示形式。 它主要用於在視窗中顯示文本文檔,但也可用於其他目的,例如工具提示中。

文字檢視引用不同類型的文本緩衝區。 該<xref:Microsoft.VisualStudio.Text.Editor.ITextView.TextViewModel%2A>屬性引用<xref:Microsoft.VisualStudio.Text.Editor.ITextViewModel>指向 這三個不同的文本緩衝區的物件:數據緩衝區(即頂部數據級緩衝區)、編輯緩衝區(其中進行編輯)和可視緩衝區(文本視圖中顯示的緩衝區)。

文本基於附加到基礎文本緩衝區的分類器進行格式化,並使用附加到文本視圖本身的修飾提供程式進行修飾。

#### <a name="the-text-view-coordinate-system"></a>文字檢視座標系

文字檢視座標系指定文字檢視中的位置。 在此座標系中,x 值 0.0 對應於顯示的文本的左邊緣,y 值 0.0 對應於顯示的文本的上邊緣。 x 座標從左到右增加,y 座標從上到下增加。

視口(文字視窗中可見的文本部分)不能以與垂直滾動相同的水準方式滾動。 視口通過更改其左側座標水準滾動,以便相對於繪圖曲面移動。 但是,只能通過更改呈現的文本垂直滾動視口,從而導致引發<xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>事件。

坐標系中的距離對應於邏輯圖元。 如果文字呈現曲面在沒有縮放變換的情況下顯示,則文本呈現座標系中的一個單位對應於顯示幕上的一個圖元。

#### <a name="margins"></a>邊界

介面<xref:Microsoft.VisualStudio.Text.Editor.ITextViewMargin>表示邊距,並能夠控制邊距的可見性及其大小。 有四個預定義的邊距,分別命名為「頂部」、「左側」、「右側」和「底部」,並附加到視圖的頂部、底部、左側或右邊緣。 這些邊距是可以放置其他邊距的容器。 介面定義返回邊距大小和邊距可見性的方法。 邊距是可視元素,提供有關它們附加到的文本視圖的其他資訊。 例如,行號邊距顯示文本視圖的行號。 字形邊距顯示 UI 元素。

介面<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider>處理邊距的創建和放置。 邊距可以相對於其他邊距進行排序。 優先順序較高的邊距位於更接近文本視圖的位置。 例如,如果有兩個邊距,邊距 A 和邊距 B,並且邊距 B 的優先順序低於邊距 A,則邊距 B 將顯示在邊距 A 的左側。

#### <a name="the-text-view-host"></a>文字檢視主機

介面<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost>包含文字檢視和伴隨檢視的任何邊裝飾,例如滾動條。 文字檢視主機還包含附加到檢視邊框的邊距。

#### <a name="formatted-text"></a>格式化文字

文字檢視中顯示的文本由<xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine>對象組成。 每個文字檢視行對應於文字檢視中的一行文本。 基礎文字緩衝區中的長行可以部分遮蓋(如果未啟用換行字),也可以分成多個文本視圖行。 介面<xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine>包含用於在座標和字元之間映射的方法和屬性,以及可能與行關聯的修飾。

<xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine>對像是使用<xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource>介面創建的。 如果您只關注檢視中目前顯示的文本,則可以忽略格式來源。 如果您對檢視中未顯示的文本格式感興趣(例如,為了支援富文本剪切和貼上),則可以使用在<xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource>文字緩衝區中設定文本的格式。

文字檢視一次設定<xref:Microsoft.VisualStudio.Text.ITextSnapshotLine>一個格式。

## <a name="editor-features"></a>編輯器功能

編輯器的功能的設計是為了讓要素的定義與其實現分開。 編輯器包括以下功能:

- 標記與分類器

- 裝飾品

- 投射

- 大綱

- 滑鼠與金鑰的結合

- 操作與基元

- IntelliSense

### <a name="tags-and-classifiers"></a>標記與分類器

標記是與文本範圍關聯的標記。 它們可以以不同的方式呈現,例如,通過使用文本著色、下劃線、圖形或彈出視窗。 分類器是一種標記。

其他類型的標記用於<xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>文本突出顯示<xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>、 大<xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>綱和 編譯錯誤。

#### <a name="classification-types"></a>分類類型

介面<xref:Microsoft.VisualStudio.Text.Classification.IClassificationType>表示等價類,它是文本的抽象類別。 分類類型可以從其他分類類型進行多重繼承。 例如,程式設計語言分類可能包括"關鍵字"、"註釋"和"標識符",它們都從"代碼"繼承。 自然語言分類類型可能包括"名詞"、"動詞"和"形容詞",它們都從"自然語言"中繼承。

#### <a name="classifications"></a>分類

分類是特定分類類型的實例,通常跨越文本範圍。 A<xref:Microsoft.VisualStudio.Text.Classification.ClassificationSpan>表示分類。 分類範圍可以視為涵蓋特定文本範圍並告訴系統此文本範圍為特定分類類型的標籤。

#### <a name="classifiers"></a>分類

<xref:Microsoft.VisualStudio.Text.Classification.IClassifier>是一種將文本分解為一組分類的機制。 必須為特定內容類型定義分類器,並為特定文本緩衝區實例化分類。 客戶端必須<xref:Microsoft.VisualStudio.Text.Classification.IClassifier>實現 才能參與文本分類。

#### <a name="classifier-aggregators"></a>類別器彙總器

分類器聚合器是一種機制,它將一個文本緩衝區的所有分類器合併為一組分類。 例如,C# 分類器和英語語言分類器都可以在 C# 檔中的註釋上創建分類。 請考慮此註解:

```
// This method produces a classifier
```

C# 分類器可能會將整個範圍標記為註釋,而英語語言分類器可能會將"生成"歸類為"動詞"和"方法"為"名詞"。 聚合器生成一組非重疊分類,並且該集合的類型基於所有貢獻。

分類器聚合器也是分類器,因為它將文本分解為一組分類。 分類器聚合器還確保沒有重疊的分類,並且對分類進行排序。 各個分類器可以按任意順序自由返回任何分類集,並以任何方式重疊。

#### <a name="classification-formatting-and-text-coloring"></a>類別格式與文字著色

文字格式是基於文本分類構建的功能的範例。 文字檢視層使用它來確定應用程式中的文本顯示。 文字格式區域取決於 WPF,但分類的邏輯定義不。

分類格式是特定分類類型的一組格式設置屬性。 這些格式從分類類型的父格式繼承。

是從<xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap>分類類型映射到一組文本格式屬性。 編輯器中格式映射的實現處理分類格式的所有匯出。

### <a name="adornments"></a>裝飾品

裝飾是與文字檢視中字元的字體和顏色沒有直接關係的圖片效果。 例如,用於標記許多程式設計語言中非編譯代碼的紅色波浪線下劃線是一種嵌入的修飾,工具提示是彈出式修飾。 修飾派生自<xref:System.Windows.UIElement>和<xref:Microsoft.VisualStudio.Text.Tagging.ITag>實現 。 兩種專用類型的修飾標記是<xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>,對於佔據與視圖中文本相同的空間的修飾,<xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>以及用於波浪線下劃線。

嵌入修飾是構成格式化文本視圖一部分的圖形。 它們以不同的 Z 順序圖層組織。 有三個內置圖層,如下所示:文本、加斯特和選擇。 但是,開發人員可以定義更多的圖層,並使它們彼此有序。 三種嵌入修飾是文本相對修飾(在文本移動時移動,刪除文本時刪除)、視圖相對修飾(與視圖的非文本部分有關)和擁有者控制的修飾(開發人員必須管理其放置)。

彈出視窗修飾是顯示在文字檢視上方的小視窗中的圖形,例如工具提示。

### <a name="projection"></a><a name="projection"></a>投影

投影是一種構造不同類型的文本緩衝區的技術,該緩衝區實際上不存儲文本,而是合併來自其他文本緩衝區的文本。 例如,投影緩衝區可用於從另外兩個緩衝區串聯文本,並將結果呈現為僅位於一個緩衝區中,或將文本的某些部分隱藏在一個緩衝區中。 投影緩衝區可以充當另一個投影緩衝區的源緩衝區。 可以構造一組由投影相關的緩衝區,以以許多不同的方式重新排列文本。 (這樣的集也稱為*緩衝區圖*。Visual Studio 文字大綱功能通過使用投影緩衝區來隱藏摺疊的文本而實現,而 ASP.NET頁的 Visual Studio 編輯器使用投影來支援嵌入的語言,如視覺基礎和 C#。

使用<xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer>建立者<xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService>使用 。 投影緩衝區由稱為<xref:Microsoft.VisualStudio.Text.ITrackingSpan>*源範圍*的物件的有序序列表示。 這些範圍的內容以字元序列的形式呈現。 從中繪製來源範圍的文字緩衝區名為*源緩衝區*。 投影緩衝區的用戶端不必知道它與普通文本緩衝區不同。

投影緩衝區偵聽源緩衝區上的文本更改事件。 當源範圍中的文本發生更改時,投影緩衝區將更改的文本座標映射到其自己的座標,並引發相應的文本更改事件。 例如,請考慮具有以下內容的源緩衝區 A 和 B:

```
A: ABCDE
B: vwxyz
```

如果投影緩衝區 P 由兩個文字範圍組成,一個具有緩衝區 A 的所有緩衝區,另一個具有所有緩衝區 B,則 P 具有以下內容:

```
P: ABCDEvwxyz
```

如果子字串`xy`從緩衝區 B 中刪除,則緩衝區 P 將引發一個事件,指示位置 7 和 8 處的字元已被刪除。

投影緩衝區也可以直接編輯。 它將編輯傳播到相應的源緩衝區。 例如,如果將字串插入到位置 6 處(字串"v"的原始位置)的緩衝區 P 中,則插入將傳播到位置 1 處的緩衝區 B。

源範圍存在導致投影緩衝區的限制。 源範圍不能重疊;因此,源範圍不能重疊。投影緩衝區中的位置不能映射到任何源緩衝區中的多個位置,並且源緩衝區中的位置不能映射到投影緩衝區中的多個位置。 源緩衝區關係中不允許迴圈。

當投影緩衝區的源緩衝區集發生更改和源範圍集更改時,將引發事件。
除去緩衝區是一種特殊的投影緩衝區。 它主要用於大綱和擴展和摺疊文本塊的操作。 消除緩衝區僅基於一個源緩衝區,並且除功能化緩衝區中的範圍必須按在源緩衝區中排序的相同。

#### <a name="the-buffer-graph"></a>緩衝區圖

該<xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph>介面支援跨投影緩衝區的圖形進行映射。 所有文本緩衝區和投影緩衝區都收集到定向的迴圈圖中,與語言編譯器生成的抽象語法樹類似。 圖形由頂部緩衝區定義,它可以是任何文本緩衝區。 緩衝區圖可以從頂部緩衝區中的點映射到源緩衝區中的點,或者從頂部緩衝區中的範圍映射到源緩衝區中的一組範圍。 同樣,它可以將點或範圍從源緩衝區映射到頂部緩衝區中的點。 使用 建立緩衝區圖時,會<xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService>使用 。

#### <a name="events-and-projection-buffers"></a>事件和投影緩衝區

修改投影緩衝區時,修改將從投影緩衝區發送到依賴於它的緩衝區。 修改所有緩衝區後,將引發緩衝區更改事件,從最深的緩衝區開始。

### <a name="outlining"></a>大綱

大綱是展開或摺疊文本視圖中不同文本塊的能力。 大綱被定義為一種<xref:Microsoft.VisualStudio.Text.Tagging.ITag>,其方式與定義修飾的方式相同。 是<xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>定義可以展開或摺疊的文本區域的標記。 要使用大綱,必須匯入<xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService>才能取得<xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager>。 大綱管理器枚舉、摺疊和展開不同的塊(表示為<xref:Microsoft.VisualStudio.Text.Outlining.ICollapsible>物件),並相應地引發事件。

### <a name="mouse-bindings"></a>滑鼠結合

滑鼠綁定將滑鼠移動連結到不同的命令。 滑鼠繫結來透過<xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider>使用 定義鍵的連結<xref:Microsoft.VisualStudio.Text.Editor.IKeyProcessorProvider>。 自動<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost>實例化所有綁定,並將它們連接到檢視中的滑鼠事件。

該<xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessor>介面包含不同滑鼠事件的預處理和後處理事件處理程式。 要處理其中一個事件,可以重寫<xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase>中的一些方法。

### <a name="editor-operations"></a>編輯器操作

編輯器操作可用於自動與編輯器交互,用於腳本或其他目的。 可以導入<xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService>以訪問給<xref:Microsoft.VisualStudio.Text.Editor.ITextView>定 上的操作。 然後,可以使用這些物件修改選擇、滾動視圖或將圖斯特移動到視圖的不同部分。

### <a name="intellisense"></a>IntelliSense

IntelliSense 支援敘述完成、簽名説明(也稱為參數資訊)、快速資訊和燈泡。

語句完成提供方法名稱、XML 元素和其他編碼或標記元素的潛在完成清單。 通常,用戶手勢調用完成會話。 會話顯示潛在完成的清單,用戶可以選擇一個或關閉清單。 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>負責建立與觸發<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession>。 計算<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>會<xref:Microsoft.VisualStudio.Language.Intellisense.CompletionSet>話的完成項。

## <a name="see-also"></a>另請參閱

- [語言服務及編輯器擴充點](../extensibility/language-service-and-editor-extension-points.md)
- [編輯器匯入](../extensibility/editor-imports.md)

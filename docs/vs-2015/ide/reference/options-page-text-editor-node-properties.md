---
title: 文字編輯器節點屬性、選項頁 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Tools Options settings, Text Editor node properties
- automation [Visual Studio], controlling Tools Options
ms.assetid: 19438302-0677-4f4d-9720-5667e6a22ab2
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: e117eac0a0a5211dcc97ddf14bf6727f62260ff8
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2019
ms.locfileid: "54767988"
---
# <a name="options-page-text-editor-node-properties"></a>文字編輯器節點屬性、選項頁
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
本文件描述與 [選項] 對話方塊的 [文字編輯器] 分類 `DTE.Properties("TextEditor", <Property Page>)` 相關聯的一些頁面 (或屬性集合)。 每一小節的標題就是用來存取 `Properties` 集合的呼叫，而每一小節中的表格會列出集合中的屬性。  
  
 [控制選項設定](http://msdn.microsoft.com/library/a09ed242-7494-4cde-bbd1-7a8ec617965d)中的 Visual Basic 巨集會示範，如何顯示 [選項] 對話方塊中每一個頁面目前的選項及其值。  
  
## <a name="general"></a>一般  
 `DTE.Properties("TextEditor", "General")`  
  
|屬性項目名稱|值|描述|  
|------------------------|-----------|-----------------|  
|GoToAnchorAfterEscape|Get/Set (布林值)|如果為 `True`，在有選取範圍時按 Escape 鍵會將插入點移至建立選取範圍這個動作的起始位置。 如果為 `False`，則會將插入點移至選取範圍的結束位置。|  
|DragNDropTextEditing|Get/Set (布林值)|決定您能否在文件中拖曳選取的文字區域，執行複製或剪貼作業。|  
|HorizontalScrollBar|Get/Set (布林值)|決定編輯器視窗上是否有水平捲軸。|  
|VerticalScrollBar|Get/Set (布林值)|決定編輯器視窗上是否有垂直捲軸。|  
|SelectionMargin|Get/Set (布林值)|決定文字窗格左邊是否有空間來執行特殊選擇作業、繪製中斷點圖示等。|  
|MarginIndicatorBar|Get/Set (布林值)|決定是否有垂直線來區隔文字窗格的左邊界與主要本文。|  
|UndoCaretActions|Get/Set (布林值)|如果 `True`. 表示復原作業除了編輯緩衝區的修改動作之外，還包含插入點動作、選擇命令等。|  
|AutoDelimiterHighlighting|Get/Set (布林值)|決定是否輸入一個結束分隔符號，讓編輯器反白顯示出開始分隔符號。 無論這個屬性的值為何，編輯器一定會以粗體顯示開始分隔符號。|  
|EditorEmulation|Get/Set (列舉)||  
|DetectUTF8WithoutSignature|Get/Set (布林值)|偵測檔案是否在沒有編碼簽章時使用 UTF-8 編碼。|  
|TrackChanges|Get/Set (布林值)||  
  
## <a name="plain-text"></a>純文字  
 `DTE.Properties("TextEditor", "PlainText")`  
  
 `PlainText` 編輯器選項會影響編輯文字檔時的編輯器設定。 每個程式語言和 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 套件都有各自特定的 [文字編輯器] 設定。 例如，若要檢視或變更 [!INCLUDE[csprcs](../../includes/csprcs-md.md)] 的編輯器設定，請使用 `DTE.Properties("TextEditor", "CSharp") or DTE.Properties("TextEditor", "CSharp-Specific")`。 [SQL 指令碼] 編輯器設定請使用 `DTE.Properties("TextEditor", "SQL ")`。  
  
|屬性項目名稱|值|描述|  
|------------------------|-----------|-----------------|  
|AutoListMembers|Get/Set (布林值)|決定當使用者在變數參考後面輸入句號時，是否自動顯示可用的成員清單|  
|AutoListParams|Get/Set (布林值)|決定當使用者在函式名稱後面輸入 "(" 時，是否自動顯示引數清單描述|  
|HideAdvancedMembers|Get/Set (布林值)|決定當陳述式完成時是否列出所有成員，或是只列出常用成員|  
|VirtualSpace|Get/Set (布林值)|決定是否將泛空白字元顯示為圖形。 如果將此屬性項目設定為 `true`，則會將此清單中的 `WordWrap` 屬性項目設定為 `false`|  
|WordWrap|Get/Set (布林值)|決定檢視表是否在字組界限處自動為長行換行。 如果將此屬性項目設定為 `true`，則會將此清單中的 `VirtualSpace` 屬性項目設定為 `false`|  
|WordWrapGlyphs|Get/Set (布林值)|在一行的結尾顯示圖像；這表示該行會換行至下一行。|  
|EnableLeftClickForURLs|Get/Set (布林值)|決定編輯器是否為 URL 加底線，以及是否只要按一下滑鼠左鍵即可跳至系統登錄之 Web 瀏覽器中的 URL|  
|IndentStyle|Get/Set (<xref:EnvDTE.vsIndentStyle>)|判斷縮排樣式：預設、智慧或無。|  
|TabSize|Get/Set (長整數)|表示一個定位點相當於幾個空格。如果設定的整數超出 1 到 60 (含) 的範圍就會失敗|  
|InsertTabs|Get/Set (布林值)|如果為 `True`，則縮排時會使用定位字元|  
|IndentSize|Get/Set (長整數)|表示一個縮排層次相當於幾個空格。 如果設定的整數值超出 1 到 60 (含) 的範圍就會失敗|  
|ShowLineNumbers|Get/Set (布林值)|決定核心編輯器文件檢視表是否在左邊界顯示行號碼|  
|ShowNavigationBar|Get/Set (布林值)|決定是否在編輯器視窗的頂端顯示下拉式清單和按鈕|  
|CutCopyBlankLines|Get/Set (布林值)|在選取時剪下或複製空白行。|  
  
## <a name="see-also"></a>請參閱  
 [控制選項設定](http://msdn.microsoft.com/library/a09ed242-7494-4cde-bbd1-7a8ec617965d)   
 [在選項頁中決定屬性項目的名稱](http://msdn.microsoft.com/library/d450422d-47c7-4eeb-9f9f-3286264bc5aa)   
 [環境節點屬性、選項頁](../../ide/reference/options-page-environment-node-properties.md)   
 [字型和色彩節點屬性、選項頁面](../../ide/reference/options-page-fonts-and-colors-node-properties.md)

---
title: 選項、文字編輯器、XML、其他
ms.date: 10/29/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XML.Miscellaneous
ms.assetid: b6538cbe-badd-4313-a1fb-39e906736bbe
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: c6def0a2e374e5297d25d17f4ea4a4a113d4bd56
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50673214"
---
# <a name="options-text-editor-xml-miscellaneous"></a>選項、文字編輯器、XML、其他
使用 [其他] 屬性頁來變更 XML 編輯器的自動完成和結構描述設定。 若要開啟 [選項] 對話方塊，請按一下 [工具] 功能表，然後按一下 [選項]。 若要存取 [其他] 屬性頁，請展開 [文字編輯器] > [XML] > [其他] 節點。

> [!NOTE]
> 根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](../../ide/personalizing-the-visual-studio-ide.md)。

## <a name="auto-insert"></a>自動插入  
**結尾標記**  
文字編輯器在撰寫 XML 項目時會新增結尾標記。 如果選取了項目起始標記，則編輯器會插入相符的結尾標記，包括相符的命名空間前置詞。 預設情況下會選取此核取方塊。  
  
**屬性引號**  
撰寫 XML 屬性時，編輯器會插入 `="` 和 `"` 字元，並將插入號 (**^**) 置於引號內。 預設情況下會選取此核取方塊。  
  
**命名空間宣告**  
編輯器會自動在需要的位置插入命名空間宣告。 預設情況下會選取此核取方塊。  
  
**其他標記 (註解、CDATA)**  
自動完成註解、CDATA、DOCTYPE、處理指示及其他標記。 預設情況下會選取此核取方塊。  
  
## <a name="network"></a>網路  
**自動下載 DTD 及結構描述**  
自動從 HTTP 位置下載結構描述及文件類型定義 (DTD)。 此功能會使用已啟用自動 Proxy 伺服器偵測的 System.Net。 預設情況下會選取此核取方塊。  
  
## <a name="outlining"></a>大綱  
**檔案開啟時進入大綱模式**  
會在檔案開始時開啟大綱功能。 預設情況下會選取此核取方塊。  
  
## <a name="caching"></a>快取  
**結構描述**  
指定結構描述快取的位置。 瀏覽按鈕 (...) 會開啟新視窗中的目前結構描述快取位置。 預設位置是 *\<Management Studio 安裝目錄>* \Xml\Schemas。  
  
## <a name="see-also"></a>另請參閱
- [如何：建立 XML 文件 (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/how-to-create-xml-documentation)
- [程式碼產生](../code-generation-in-visual-studio.md)

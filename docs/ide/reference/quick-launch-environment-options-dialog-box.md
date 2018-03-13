---
title: "選項對話方塊、環境、快速啟動 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Environment.QuickLaunch
- vs.quicklaunch
helpviewer_keywords:
- searching IDE
- IDE, searching
ms.assetid: 4200f297-d065-4723-9a30-d91ff2e26c9d
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 0f71cca51a27c8ed9d6467d99425d4d3b721d195
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="quick-launch-environment-options-dialog-box"></a>選項對話方塊、環境、快速啟動
您可以使用 [快速啟動] 快速搜尋選項、範本、功能表這類 IDE 資產，並對其執行動作。 但無法使用 [快速啟動] 來搜尋程式碼和符號。 [快速啟動] 搜尋方塊位於功能表列的右上角，而且選擇 Ctrl+Q 鍵即可存取。 只要在方塊中輸入搜尋字串即可。 若要搜尋包含 @ 的字串，請使用 ”@@”。  
  
 當您安裝 Visual Studio 時，預設會啟用 [快速啟動]。 您可以在功能表列上顯示或隱藏 [快速啟動]，方法是依序選擇 [工具] 和 [選項]。 展開 [環境] 節點，然後選擇 [快速啟動]。 選取或清除 [啟用快速啟動] 核取方塊。 您也可以啟用或停用這個頁面上的搜尋分類。  
  
## <a name="category-list"></a>分類清單  
 [快速啟動] 搜尋結果會出現在四個分類中：[最近用過的函式]、[功能表]、[選項] 和 [開啟文件]，並提供該分類的項目數。 若要依分類來周遊搜尋結果，請選擇 Ctrl+Q 鍵顯示下一個分類中的所有結果。 最後一個分類出現之後，Ctrl+Q 會顯示每個分類中的幾個結果。 您可以使用 Ctrl+Shift+Q 以反向順序巡覽分類。 若要檢視某個分類底下的所有搜尋結果，請選擇該分類名稱。  
  
 您可以使用下列快速鍵，限制搜尋特定分類。  
  
|分類|快速鍵|快速鍵描述|  
|--------------|--------------|--------------------------|  
|最近使用|@mru<br /><br /> 例如：`@mru font`|最多顯示您 [最近用過的函式] 的五個項目。|  
|Menus|@menu<br /><br /> 例如：`@menu font`|限制搜尋功能表項目。|  
|選項|@opt<br /><br /> 例如：`@opt font`|限制搜尋 [選項] 對話方塊中的設定。|  
|文件|@doc<br /><br /> 例如：`@doc font`|限制搜尋符合搜尋準則之開啟文件的檔案名稱和路徑，但不會搜尋檔案本身內的文字。|  
  
> [!NOTE]
>  您可以在 [選項] 對話方塊的 [一般] 和 [鍵盤] 頁面上，變更快速鍵。  
  
## <a name="show-previous-results"></a>顯示先前的結果  
 根據預設，您輸入的搜尋字詞不會在搜尋工作階段之間保留。 如果您搜尋某個字詞，然後將游標移出 [快速啟動] 區域再移回，則會清除搜尋字串。 若要保留搜尋結果，請移至 [選項] 對話方塊，並選擇 [快速啟動]，然後選取 [啟用快速啟動時顯示前一個搜尋的搜尋結果]。 核取方塊。 下次您執行搜尋、離開 [快速啟動] 區域並返回時，[快速啟動] 將會保留上次使用的搜尋字詞，也會顯示搜尋結果。  
  
 如需使用 [快速啟動] 的最新祕訣和訣竅，請參閱 [Visual Studio 部落格](http://go.microsoft.com/fwlink/?LinkId=236054)。  
  
## <a name="see-also"></a>請參閱  
 [一般使用者介面項目 (Visual Studio)](../../ide/reference/general-user-interface-elements-visual-studio.md)   
 [環境選項對話方塊](../../ide/reference/environment-options-dialog-box.md)
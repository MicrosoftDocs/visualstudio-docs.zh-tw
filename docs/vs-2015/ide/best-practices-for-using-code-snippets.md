---
title: 使用程式碼片段的最佳做法 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- code snippets, best practices
- code snippets, security
ms.assetid: a293ec17-4dd7-4a99-8eeb-99f44a822a8b
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 750d96442f59c29a8e565e6b57eda292656ad1f7
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54770313"
---
# <a name="best-practices-for-using-code-snippets"></a>使用程式碼片段的最佳作法
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

程式碼片段中的程式碼只會顯示最基本的做法。 對於大部分的應用程式，此程式碼必須經過修改以符合應用程式。  
  
## <a name="handling-exceptions"></a>例外狀況處理  
 一般來說，程式碼片段 Try…Catch 區塊會攔截並重新擲回所有例外狀況。 不過，這並不一定適用於您的專案。 對於每個例外狀況而言，有數種回應的方法。 如需範例，請參閱[如何：處理例外狀況使用 try/catch (C#程式設計指南)](http://msdn.microsoft.com/library/ca8e3773-980e-4767-8633-7408540e9818)並[試...Catch...Try...catch...finally 陳述式](http://msdn.microsoft.com/library/d6488026-ccb3-42b8-a810-0d97b9d6472b)。  
  
## <a name="file-locations"></a>檔案位置  
 當您調整應用程式的檔案位置時，請考慮下列事項：  
  
-   尋找可存取的位置。 使用者可能無法存取電腦的 Program Files 資料夾，因此儲存檔案和應用程式檔案的作業可能無法正常運作。  
  
-   尋找安全位置。 將檔案儲存在根資料夾 (C:\\) 並不安全。 若是應用程式資料，建議儲存在 \Application Data 資料夾。 若是個別使用者資料，應用程式可以在 \My Documents 資料夾中為每位使用者建立檔案。  
  
-   使用有效的檔案名稱。 您可以使用 <xref:System.Windows.Forms.OpenFileDialog> 和 <xref:System.Windows.Forms.SaveFileDialog> 控制項，從而減少發生無效檔案名稱的可能性。 請注意，從使用者選取檔案到您的程式碼管理檔案的這段時間，檔案可能會遭到刪除。 此外，使用者可能沒有寫入檔案的權限。  
  
## <a name="security"></a>安全性  
 程式碼片段的安全程度會視其在原始程式碼中的使用位置，以及位於程式碼之後的修改方式而定。 下列清單包含一些必須考量的部分。  
  
- 檔案和資料庫存取  
  
- 程式碼存取安全性  
  
- 保護資源 (例如事件記錄檔、登錄)  
  
- 儲存密碼  
  
- 驗證輸入  
  
- 將資料傳遞至指令碼技術  
  
  如需詳細資訊，請參閱[設定應用程式的安全性](../ide/securing-applications.md)。  
  
## <a name="downloaded-code-snippets"></a>已下載的程式碼片段  
 Visual Studio 所安裝的 IntelliSense 程式碼片段本身並沒有安全性方面的危險。 不過，這些程式碼片段在您的應用程式中可能會產生安全性風險。 從網際網路下載的程式碼片段應視為任何其他下載的內容，因此必須格外謹慎處理。  
  
-   只從您信任的網站下載程式碼片段，並使用最新的防毒軟體。  
  
-   在 [記事本] 或 Visual Studio 的 XML 編輯器中開啟所有下載的程式碼片段檔案，並仔細檢閱後再進行安裝。 尋找下列問題：  
  
    -   程式碼片段的程式碼可能會在執行時損害您的系統。 執行前，請仔細閱讀原始程式碼。  
  
    -   程式碼片段檔案的說明 URL 區塊可能包含執行惡意指令碼檔的 URL，或包含具攻擊性網站的 URL。  
  
    -   程式碼片段可能包含以無訊息模式新增至專案，而且可能會從您系統上的任何位置載入的參考。 這些參考可能已從您下載程式碼片段的位置下載到您的電腦。 程式碼片段可能會接著呼叫參考中執行惡意程式碼的方法。 為了保護您自己免於遭受這類攻擊，請檢閱程式碼片段檔案的匯入和參考區塊。  
  
## <a name="see-also"></a>請參閱  
 [Visual Basic IntelliSense 程式碼片段](http://msdn.microsoft.com/library/ffdde4c9-8141-4906-b09b-15181357a643)   
 [設定應用程式的安全性](../ide/securing-applications.md)   
 [程式碼片段](../ide/code-snippets.md)

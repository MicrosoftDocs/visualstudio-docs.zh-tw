---
title: 使用程式碼片段的最佳作法
description: 瞭解程式碼片段、程式碼片段的意圖，以及如何使用它們來配合您的應用程式。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- code snippets, best practices
- code snippets, security
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ad94fb8ea4dffcd0c3c7c10bb06046d5558baa1e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99836497"
---
# <a name="best-practices-for-using-code-snippets"></a>使用程式碼片段的最佳做法

程式碼片段中的程式碼只會顯示最基本的做法。 對於大部分的應用程式，此程式碼必須經過修改以符合應用程式。

## <a name="handling-exceptions"></a>處理例外狀況

一般來說，程式碼片段 Try...Catch 區塊會攔截並重新擲回所有例外狀況。 不過，這並不一定適用於您的專案。 對於每個例外狀況而言，有數種回應的方法。 如需範例，請參閱[如何：使用 try/catch 處理例外狀況 (C#)](/dotnet/csharp/programming-guide/exceptions/how-to-handle-an-exception-using-try-catch) 和 [Try...Catch...Finally 陳述式 (Visual Basic)](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)。

## <a name="file-locations"></a>檔案位置

當您調整應用程式的檔案位置時，請考慮下列事項：

- 尋找可存取的位置。 使用者可能無法存取電腦的 *Program Files* 資料夾，因此應用程式檔案的存檔作業可能無法正常運作。

- 尋找安全位置。 將檔案儲存在根資料夾 (*C： \\*) 並不安全。 針對應用程式資料，我們建議 *應用程式資料* 資料夾。 若是個別使用者資料，應用程式可以在 *Documents* 資料夾中為每位使用者建立檔案。

- 使用有效的檔案名稱。 您可以使用 <xref:System.Windows.Forms.OpenFileDialog> 和 <xref:System.Windows.Forms.SaveFileDialog> 控制項，從而減少發生無效檔案名稱的可能性。 請注意，從使用者選取檔案到您的程式碼管理檔案的這段時間，檔案可能會遭到刪除。 此外，使用者可能沒有寫入檔案的權限。

## <a name="security"></a>安全性

程式碼片段的安全程度會視其在原始程式碼中的使用位置，以及位於程式碼之後的修改方式而定。 下列清單包含一些必須考量的部分。

- 檔案和資料庫存取

- 程式碼存取安全性

- 保護資源 (例如事件記錄檔、登錄)

- 儲存祕密

- 驗證輸入

- 將資料傳遞至指令碼技術

如需詳細資訊，請參閱[保護應用程式](../ide/securing-applications.md)。

## <a name="downloaded-code-snippets"></a>已下載的程式碼片段

Visual Studio 所安裝的 IntelliSense 程式碼片段本身並沒有安全性方面的危險。 不過，這些程式碼片段在您的應用程式中可能會產生安全性風險。 從網際網路下載的程式碼片段應視為任何其他下載的內容，因此必須格外謹慎處理。

- 只從您信任的網站下載程式碼片段，並使用最新的防毒軟體。

- 在 [記事本] 或 Visual Studio 的 XML 編輯器中開啟所有下載的程式碼片段檔案，並仔細檢閱後再進行安裝。 尋找下列問題：

  - 程式碼片段的程式碼可能會在執行時損害您的系統。 執行前，請仔細閱讀原始程式碼。

  - 程式碼片段檔案的說明 URL 區塊可能包含執行惡意指令碼檔的 URL，或包含具攻擊性網站的 URL。

  - 程式碼片段可能包含以無訊息模式新增至專案，而且可能會從您系統上的任何位置載入的參考。 這些參考可能已從您下載程式碼片段的位置下載到您的電腦。 程式碼片段可能會接著呼叫參考中執行惡意程式碼的方法。 為了保護您自己免於遭受這類攻擊，請檢閱程式碼片段檔案的匯入和參考區塊。

## <a name="see-also"></a>另請參閱

- [Visual Basic IntelliSense 程式碼片段](/dotnet/visual-basic/developing-apps/using-ide/intellisense-code-snippets)
- [保護應用程式](../ide/securing-applications.md)
- [程式碼片段](../ide/code-snippets.md)

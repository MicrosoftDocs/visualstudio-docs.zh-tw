---
title: 針對中斷參考進行疑難排解
description: 瞭解如何針對可能由應用程式無法尋找參考元件的其他內容所造成的中斷參考進行疑難排解。
ms.custom: SEO-VS-2020
ms.date: 03/21/2017
ms.topic: troubleshooting
helpviewer_keywords:
- C# projects, references
- Visual Basic projects, references
- troubleshooting references
- referencing files from projects
- referencing components, troubleshooting
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 627724410ac9e0829faeb23cb5b0eef01b153293
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2020
ms.locfileid: "96479169"
---
# <a name="troubleshoot-broken-references"></a>針對中斷參考進行疑難排解

如果您的應用程式嘗試使用中斷的參考，則會產生例外狀況錯誤。 此錯誤的主要原因是找不到參考的元件，但在某些情況下也可能將參考視為中斷。 下列清單顯示這些情況：

- 專案的參考路徑不正確或不完整。

- 參考的檔案已被刪除。

- 參考的檔案已被重新命名。

- 網路連線或驗證失敗。

- 參考未安裝在電腦上的 COM 元件。

以下是這些問題的補救方法。

> [!NOTE]
> 組件中的檔案是使用專案檔中的絕對路徑來參考的。 因此，在多開發人員環境中工作的使用者，可能會遺漏本機環境中參考的組件。 若要避免這些錯誤，您最好在這些情況下新增專案對專案參考。 如需詳細資訊，請參閱[使用組件設計程式](/dotnet/framework/app-domains/programming-with-assemblies)。

## <a name="reference-path-is-incorrect"></a>參考路徑不正確

如果在不同的電腦上共用專案，則當元件位於每部電腦的不同目錄時，可能會找不到某些參考。 參考會儲存在元件檔名稱 (例如 *MyComponent*) 之下。 將參考新增至專案時，會將元件檔的資料夾位置 (例如 *C:\MyComponents*) 附加至 **ReferencePath** 專案屬性。

當專案開啟時，它會藉由尋找參考路徑中的目錄，嘗試找出這些參考的元件檔。 如果用來開啟專案的電腦將元件儲存在不同的目錄 (例如 *D:\MyComponents*)，則找不到參考且 [工作清單] 中會出現錯誤。

若要修正這個問題，您可以刪除中斷的參考，然後使用 [加入參考] 對話方塊將它取代。 另一個解決方法是使用專案屬性頁中的 [參考路徑] 項目，然後修改清單中的資料夾以指向正確的位置。 每部電腦上每位使用者的 [參考路徑] 屬性都會保留。 因此，修改您的參考路徑並不會影響專案的其他使用者。

> [!TIP]
> 專案對專案參考沒有這些問題。 因此，請盡可能以此取代檔案參考。

### <a name="to-fix-a-broken-project-reference-by-correcting-the-reference-path"></a>藉由修正參考路徑來修復中斷的專案參考

1. 在方案總管中，以滑鼠右鍵按一下您的專案節點，然後按一下 [屬性]。

   [ **專案設計** 工具] 隨即出現。

1. 如果使用 Visual Basic，請選取 [參考] 頁面，然後按一下 [參考路徑] 按鈕。 在 [參考路徑] 對話方塊的 [資料夾] 欄位中，輸入包含所要參考之項目的資料夾路徑，然後按一下 [加入資料夾] 按鈕。

    如果使用 C#，請選取 [參考路徑] 頁面。 在 [資料夾] 欄位中，輸入包含所要參考之項目的資料夾路徑，然後按一下 [加入資料夾] 按鈕。

## <a name="referenced-file-has-been-deleted"></a>參考的檔案已被刪除

參考的檔案有可能已被刪除，而不再存在於磁碟機中。

### <a name="to-fix-a-broken-project-reference-for-a-file-that-no-longer-exists-on-your-drive"></a>為磁碟機中已不存在的檔案修復中斷的專案參考

- 刪除參考。

- 如果電腦上的其他位置已有此參考，請從該位置讀取。

## <a name="referenced-file-has-been-renamed"></a>參考的檔案已被重新命名

參考的檔案有可能已被重新命名。

### <a name="to-fix-a-broken-reference-for-a-file-that-has-been-renamed"></a>為已重新命名的檔案修復中斷的參考

- 刪除參考，然後新增已重新命名的檔案參考。

- 如果電腦上的其他位置已有此參考，您必須從該位置讀入。

## <a name="network-connection-or-authentication-has-failed"></a>網路連線或驗證失敗

造成檔案無法存取的原因可能有許多；例如，網路連線失敗或驗證失敗。 每個原因可能都有獨特的修復方法；例如，您可能必須連絡本機系統管理員以存取必要資源。 不過，刪除參考並修復使用它的程式碼一定是可行的方法。

## <a name="com-component-is-not-installed-on-computer"></a>COM 元件未安裝在電腦上

如果一位使用者加入了 COM 元件的參考，而第二位使用者嘗試在未安裝此元件的電腦上執行程式碼，則第二位使用者將收到參考中斷的錯誤。 在第二部電腦上安裝元件將會修正此錯誤。 如需如何在專案中使用 COM 元件參考的詳細資訊，請參閱 [.NET Framework 應用程式中的 com 互通性](/dotnet/visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications)。

## <a name="see-also"></a>另請參閱

- [專案設計工具，參考頁 (Visual Basic)](../ide/reference/references-page-project-designer-visual-basic.md)

---
title: 將特定 Guid 指派給 Visual Studio 訂閱者 |Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 04/20/2020
ms.topic: conceptual
description: 瞭解系統管理員如何對訂閱者進行特定的訂用帳戶 GUID
ms.openlocfilehash: e6c50239721d810964f2b95e0ec3509999d2f4d5
ms.sourcegitcommit: 9a7fb8556a5f3dbb4459122fefc7e7a8dfda753a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87235182"
---
# <a name="assign-specific-subscriptions-in-the-visual-studio-subscriptions-administration-portal"></a>在 Visual Studio 訂用帳戶系統管理入口網站中指派特定訂閱

系統管理員現在可以使用 Visual Studio 訂用帳戶管理入口網站，將特定訂閱指派給個別的訂閱者。  當組織有暫時的員工或需要在短時間記憶體取訂用帳戶的廠商時，這項功能就很有用。  系統管理員可以指派已經部分使用的訂用帳戶，讓其新訂閱更長期使用。  

<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4t4cl]


## <a name="assign-specific-subscription-guids-to-users"></a>將特定的訂用帳戶 Guid 指派給使用者

將特定訂用帳戶指派給個人的程式，牽涉到利用兩個現有的系統管理程式，將特定的訂用帳戶全域唯一識別碼（Guid）指派給個別使用者。  這三個步驟的套裝程式括匯出目前訂用帳戶和指派的清單、使用該清單來識別您想要指派的特定 Guid，然後使用大量新增程式來上傳新的指派。

### <a name="export-your-subscriptions-information"></a>匯出訂閱資訊

執行匯出：
1. 登入系統[管理入口網站](https://manage.visualstudio.com)。
2. 選取 [匯出]**** 索引標籤，檔案就會下載到您的本機電腦。 針對包含您使用者訂用帳戶的合約，檔案中會有合約的名稱，以及匯出的日期。
> [!div class="mx-imgBorder"]
> ![匯出訂閱者](_img/exporting-subscriptions/exporting-subscriptions.png "按一下 [匯出]，以使用訂閱者資訊儲存已指派訂閱的清單。")

### <a name="identify-the-guids-you-want-to-assign"></a>識別您想要指派的 Guid

如果您先前使用過匯出工具，您會發現新的欄位已新增至所產生的試算表中。  這些可協助您判斷每個訂閱的狀態，以及您要指派給使用者的訂用帳戶。  

- **訂**用帳戶狀態：此欄位會指出「已指派」或「未指派」。  如果訂用帳戶的狀態為「已指派」，它也會有與其相關聯的使用者資訊，例如名稱、電子郵件等。 
- **使用狀態**：使用狀態會指出「新增」，表示它從未指派給使用者，或「已使用」，表示已在某個時間點將其指派給使用者。  

您可以使用這些欄位中的值和試算表中的其他資訊，來決定您想要指派給個別使用者的訂閱。 您可以在 Excel 中套用篩選，以協助依據狀態、訂閱等級、到期日等範圍來縮小清單。 

### <a name="upload-your-new-assignments"></a>上傳您的新指派

最後一個步驟是下載**大量新增**範本，並填寫您想要指派之訂用帳戶的必要資訊，然後上傳範本。  如需該程式的完整說明，請參閱[新增多個使用者](assign-license-bulk.md)文章。  

> [!IMPORTANT]
> 若要確保成功上傳，請確定：
> - 當您選取 [**大量新增**] 時，您會使用對話方塊中連結的範本。  請勿使用範本的本機儲存複本，因為它可能不會包含所有必要的欄位。  使用舊範本會導致上傳失敗。 
> - 在範本中顯示為**必要**的所有欄位都已完成。
> - [**錯誤訊息**] 欄中沒有列出任何錯誤。
> - 每個 GUID 只會在範本中使用一次。 
> - 範本中的訂用帳戶層級符合匯出清單中 GUID 的訂用帳戶。 
> - GUID 尚未指派給匯出清單中的另一位使用者。 

## <a name="frequently-asked-questions"></a>常見問題集
### <a name="qhow-do-i-change-which-subscription-is-currently-assigned-to-an-individual-user"></a>Q:How 是否要變更目前指派給個別使用者的訂用帳戶？
答：如果您想要變更指派給使用者的 GUID，您必須先刪除該使用者的訂用帳戶。  如需詳細資訊，請參閱我們的[刪除訂閱](delete-license.md)文章以取得詳細資訊。  刪除該使用者的訂用帳戶之後，請使用上面所述的程式來匯出清單並上傳新的訂用帳戶資訊。  

## <a name="see-also"></a>另請參閱
- [Visual Studio 文件](/visualstudio/)
- [Azure DevOps 檔](/azure/devops/)
- [Azure 文件](/azure/)
- [Microsoft 365 檔](/microsoft-365/)

## <a name="next-steps"></a>後續步驟
現在您已指派訂閱給使用者，請瞭解如何執行其他管理工作。
- [指派個別訂閱](assign-license.md)
- [指派多個訂用帳戶](assign-license-bulk.md)
- [編輯訂用帳戶](edit-license.md)
- [刪除訂用帳戶](delete-license.md)
- [判斷最大使用量](maximum-usage.md)



---
title: 將特定 Guid 指派給 Visual Studio 訂閱者 |Microsoft 檔
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.date: 02/18/2021
ms.topic: conceptual
description: 瞭解系統管理員如何對訂閱者進行特定訂用帳戶 GUID
ms.openlocfilehash: 3c92a3e6cc35230f6bcf10320e92a50dc5ffb85b
ms.sourcegitcommit: 79a6be815244f1cfc7b4123afff29983fce0555c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2021
ms.locfileid: "102249676"
---
# <a name="assign-specific-subscriptions-in-the-visual-studio-subscriptions-administration-portal"></a>在 Visual Studio 訂用帳戶管理入口網站中指派特定訂閱

系統管理員現在可以使用 Visual Studio 訂用帳戶管理入口網站，將特定訂用帳戶指派給個別的訂閱者。  如果組織有暫時的員工或廠商需要存取訂用帳戶一小段時間，這項功能就很有用。  系統管理員可以指派已部分使用的訂用帳戶，讓新的訂用帳戶更長期使用。  

觀賞影片或繼續閱讀，以瞭解如何將特定訂閱 Guid 指派給使用者。 

<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4t4cl]


## <a name="assign-specific-subscription-guids-to-users"></a>將特定訂用帳戶 Guid 指派給使用者

將特定訂用帳戶指派給個人的程式牽涉到利用兩個現有的系統管理員程式，將特定訂用帳戶全域唯一識別碼 (Guid) 指派給個別使用者。  三個步驟的套裝程式括匯出您目前的訂用帳戶和指派清單、使用該清單來識別您想要指派的特定 Guid，然後使用大量新增程式來上傳新的指派。

### <a name="export-your-subscriptions-information"></a>匯出訂閱資訊

執行匯出：
1. 登入系統 [管理入口網站](https://manage.visualstudio.com)。
2. 選取 [匯出] 索引標籤，檔案就會下載到您的本機電腦。 針對包含您使用者訂用帳戶的合約，檔案中會有合約的名稱，以及匯出的日期。
> [!div class="mx-imgBorder"]
> ![匯出訂閱者](_img/exporting-subscriptions/exporting-subscriptions.png "按一下 [匯出]，以訂閱者資訊儲存指派的訂閱清單。")

### <a name="identify-the-guids-you-want-to-assign"></a>識別您想要指派的 Guid

如果您先前曾使用過匯出工具，您會發現新的欄位已加入至產生的試算表中。  這些將協助您判斷每個訂用帳戶的狀態，以及您想要指派給使用者的訂用帳戶狀態。  

- **訂** 用帳戶狀態：此欄位會指出「已指派」或「未指派」。  如果訂用帳戶的狀態為「已指派」，則它也會有與其相關聯的使用者資訊，例如名稱、電子郵件等等。 
- **使用狀態**：使用狀態會指出「新增」，表示從未指派給使用者，或「已使用」表示已在某個時間點指派給使用者。  

您可以使用這些欄位中的值以及試算表中的其他資訊，來決定您要指派給個別使用者的訂閱。 您可以在 Excel 中套用篩選準則，以協助依狀態、訂用帳戶層級、到期日等來縮小清單的範圍。 

### <a name="upload-your-new-assignments"></a>上傳新的指派

最後一個步驟是下載 **大量新增** 範本、填寫您要指派之訂用帳戶的必要資訊，然後上傳範本。  如需該程式的完整說明，請參閱我們的 [新增多位使用者](assign-license-bulk.md) 文章。  

> [!IMPORTANT]
> 為確保成功上傳，請確定：
> - 當您選取 [ **大量新增**] 時，會使用對話方塊中連結的範本。  請勿使用本機儲存的範本複本，因為它可能不包含所有必要的欄位。  使用舊範本將會導致上傳失敗。 
> - 所有在範本中顯示為 **必要** 的欄位都已完成。
> - **錯誤訊息** 資料行中沒有列出任何錯誤。
> - 每個 GUID 只會在範本中使用一次。 
> - 範本中的訂用帳戶層級與匯出清單中的 GUID 訂用帳戶相符。 
> - GUID 尚未指派給匯出清單中的另一位使用者。 

## <a name="frequently-asked-questions"></a>常見問題集
### <a name="q-how-do-i-change-which-subscription-is-currently-assigned-to-an-individual-user"></a>問：如何變更目前指派給個別使用者的訂用帳戶？
答：如果您想要變更指派給使用者的 GUID，您必須先刪除該使用者的訂用帳戶。  如需詳細資訊，請參閱我們的 [刪除訂閱](delete-license.md) 文章，以取得詳細資訊。  刪除該使用者的訂用帳戶之後，請使用上面所述的程式來匯出清單並上傳新的訂用帳戶資訊。  

## <a name="resources"></a>資源
- [訂閱支援](https://visualstudio.microsoft.com/subscriptions/support/)

## <a name="see-also"></a>另請參閱
- [Visual Studio 檔](/visualstudio/)
- [Azure DevOps 文件](/azure/devops/) \(英文\)
- [Azure 檔](/azure/)
- [Microsoft 365 檔](/microsoft-365/)

## <a name="next-steps"></a>下一步
現在您已將訂用帳戶指派給使用者，請瞭解如何執行其他系統管理工作。
- [指派個別訂用帳戶](assign-license.md)
- [指派多個訂用帳戶](assign-license-bulk.md)
- [編輯訂用帳戶](edit-license.md)
- [刪除訂用帳戶](delete-license.md)
- [判斷最大使用量](maximum-usage.md)



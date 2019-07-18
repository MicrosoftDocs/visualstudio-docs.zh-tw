---
title: Visual Studio Enterprise 和 Visual Studio Professional 雲端訂閱帳單常見問題集
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 03/02/2018
ms.topic: conceptual
description: 雲端訂用帳戶帳單問題。
ms.openlocfilehash: 858707358062386191c526810644f110bd7ac58d
ms.sourcegitcommit: f369ff7e84b0216f01570a486c7be80ca6d0e61a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68250728"
---
# <a name="visual-studio-cloud-subscriptions-billing-faq"></a>Visual Studio 雲端訂閱帳單常見問題集

請務必[比較雲端訂閱權益和定價](https://visualstudio.microsoft.com/vs/pricing/)，利用雲端與標準 Visual Studio 訂閱之間的比較、訂閱者權益的詳細資料以及其他更多，了解每個 Visual Studio 訂用帳戶的權益。

## <a name="general-purchasing-questions"></a>一般購買問題

### <a name="q-can-i-buy-visual-studio-cloud-subscriptions-using-a-purchase-order"></a>問：是否可以使用訂購單來購買 Visual Studio 雲端訂用帳戶？
答：否。 所有的 Visual Studio 雲端訂閱都必須使用 Azure 訂用帳戶購買。 (請把它想像為您的 Azure 計費帳戶。)

### <a name="q-what-types-of-azure-subscriptions-can-be-used-to-buy-visual-studio-cloud-subscriptions"></a>問：什麼類型的 Azure 訂用帳戶可以用來購買 Visual Studio 雲端訂用帳戶？
答：可以使用大部分 Azure 訂用帳戶；我們支援連線至 [Enterprise 合約 (EA)](https://azure.microsoft.com/pricing/enterprise-agreement/) 的 Azure 訂用帳戶、雲端解決方案提供者 (CSP) 所設定的 Azure 訂用帳戶、透過 Microsoft Open License 轉銷商所設定的 Azure 訂用帳戶，以及隨用隨付 Azure 訂用帳戶。

無法使用某些類型的 Azure 訂用帳戶 (包括 [Azure 免費試用](https://azure.microsoft.com/pricing/free-trial/) 以及併入為 Visual Studio 訂用帳戶中訂閱者權益的訂用帳戶)。

### <a name="q-am-i-required-to-buy-other-azure-services"></a>問：我必須購買其他 Azure 服務嗎？
答：完全不用。 如果您只想要透過 Azure 購買 Visual Studio 雲端訂閱，您可以就這麼做。

## <a name="enterprise-agreement-ea-customers"></a>Enterprise 合約 (EA) 客戶

### <a name="q-can-i-use-an-enterprise-agreement-to-buy-visual-studio-cloud-subscriptions"></a>問：是否可以使用 Enterprise 合約購買 Visual Studio 雲端訂用帳戶？

答：可以。 您必須是為 EA 所建立之 Azure 訂用帳戶的擁有者或參與者。 請確定您是直接在 Visual Studio Marketplace 購買 Visual Studio 雲端訂閱。 您不可以使用訂單購買 Visual Studio 雲端訂閱？

### <a name="q-how-can-i-tell-whether-i-have-the-necessary-privileges-to-buy-services-in-the-visual-studio-marketplace-through-my-organizations-enterprise-agreement"></a>問：如何判斷我是否有必要的權限，可透過我組織的 Enterprise 合約在 Visual Studio Marketplace 中購買服務？

答：判斷您是否擁有正確權限最簡單的方法是按一下 Visual Studio Marketplace 提供的服務 [購買]  按鈕。
您需要從目前連結到您登入之 Azure 訂用帳戶提供的清單中選取 Azure 訂用帳戶 (這是計費帳戶)。
因為 Azure 訂用帳戶的名稱預設為計費帳戶類型 (「隨用隨付方案」、「Enterprise 合約」等等)，Azure 訂用帳戶是否屬於 Enterprise 合約通常很清楚。

另一個方法是嘗試瀏覽 [Azure 企業版入口網站](https://ea.azure.com)。  如果您可以成功連線，您即有企業系統管理員或帳戶擁有者角色。 只有帳戶擁有者可以在 Enterprise 合約中設定新的 Azure 計費帳戶。 如果您無法存取 Azure 企業版入口網站，請在組織內詢問，找到您的企業系統管理員，然後要求該人員將您新增為 Azure 企業版入口網站的帳戶擁有者。  如果您找不到這位人員，您可以[提交支援票證](https://aka.ms/AzureEntSupport)並要求連絡資訊。  支援票證需要有您組織的名稱和您的 Enterprise 合約註冊號碼。

### <a name="q-can-i-use-the-azure-monetary-commitment-funds-from-my-enterprise-agreement-to-buy-visual-studio-cloud-subscriptions"></a>問：是否可以使用 Enterprise 合約的 Azure 預付金購買 Visual Studio 雲端訂用帳戶？

答：不行，預付金不適合購買 Visual Studio 雲端訂用帳戶。 當您選擇用為您的 EA 建立的 Azure 訂用帳戶購買 Visual Studio 雲端訂閱時，費用會出現在您下一次的「超額」發票上。 通常是每月一次，但因部分 EA 客戶的歷程記錄規則，超額發票可能幾個月都不會發出。 請洽詢您的 EA 授權專家，您是否需要知道哪些額外購買數量 (即不適合使用 Azure 預付金購買的項目) 會觸發超額發票。

## <a name="how-charges-are-processed"></a>收費方式

### <a name="q-how-are-monthly-cloud-subscription-charges-processed"></a>問：雲端訂用帳戶的**月租方案**如何收費？
答：首次購買時，我們會依當月剩餘天數按比例分配的數量來計價。 例如，如果在 4 月 15 日購買了 10 個 Visual Studio Professional 雲端訂閱月租方案，我們會收取 5 個單位的費用，因為該月只剩 50% 的費用 (4 月有 30 天，還剩下 15 天)。
自 5 月 1 日起至您取消前的每個月，會依完整的 10 個單位計費。

稍後當您增加付費數量時，我們也會將增加的單位按比例分配至當月的剩餘天數。 因此，如果您在 5 月 10 日購買 1 個以上的 Visual Studio Professional 雲端訂閱月租方案，我們大約收取 0.677 個單位的費用 (5 月有 31 天，還有 21 天)。

### <a name="q-how-are-annual-cloud-subscription-charges-processed"></a>問：雲端訂用帳戶的**年度訂用帳戶**如何收費？
答：每次購買都是立即按購買的完整數量計價。 費用不會分散到一整年，也不會按比例分配。 如果您在一年的不同時間分次購買年度的雲端訂閱，您必須在不同的月份續約訂閱。 我們不會將客戶所有的年度雲端訂閱連在一起，雖然這在 Microsoft 大量授權合約購買中很常見。

### <a name="q-how-do-cancelations-work"></a>問：取消如何運作？
答：當您取消 Visual Studio 雲端訂用帳戶時，您即取消自動續約。 訂閱保持有效直至其正常的續約日期，然後就到期。
到期時，Visual Studio 訂閱者即無法再使用 Visual Studio 或來自訂用帳戶的任何其他權益。

雲端訂閱月租方案的取消會在次月一日生效。 如果您只取消部分雲端訂閱月租方案，請務必於次月一日移除使用者，以確保正確的使用者能繼續獲指派有效的訂用帳戶。

至於年度雲端訂閱，取消要到原購買起算 12 個月後的該月一日才會生效，或自上次年度續約收費起算 12 個月後生效。 例如，如果您在 2018 年 1 月 3 日購買了 Visual Studio Professional 年度雲端訂用帳戶，當此訂用帳戶自動續訂一年時，就會一直保持有效到 2019 年 2 月 1 日。 如果您這個日期和 2020 年 2 月 1 日之間的任何時間取消訂閱，則此訂閱會在 2020 年 2 月 1 日到期。 取消方在年度雲端訂閱的訂閱年度中不會有任何退款。

### <a name="q-what-kind-of-volume-discounts-are-available-for-visual-studio-subscriptions"></a>問：Visual Studio 訂用帳戶有哪些大量採購折扣？

答：「每種類型」  的訂用帳戶，自第 6 個開始，所有後續訂用帳戶都會獲得 5% 的折扣：

* Visual Studio Professional 每月
* Visual Studio Professional 年度
* Visual Studio Enterprise 每月
* Visual Studio Enterprise 年度

例如，如果您購買 6 個 Visual Studio Professional 訂閱月租方案以及 5 個 Visual Studio Enterprise 訂閱月租方案，您的 5 個 Professional 要支付一般價格，第 6 個 Professional 有 5% 的折扣，而 5 個 Enterprise 訂閱則全都要支付一般價格。

而且，折扣僅適用於指定的月租方案計費期費用。 因此，如果您在一個月內購買了 5 個 Visual Studio Professional 訂閱的年度訂閱，然後在次月又購買了 5 個，則所有 10 個訂閱都要支付一般價格。

> [!NOTE]
> Microsoft 不再於雲端訂用帳戶中提供 Visual Studio Professional 年度訂用帳戶和 Visual Studio Enterprise 年度訂用帳戶。 現有的客戶體驗，以及更新、增加、減少或取消其訂用帳戶的能力將不會改變。 我們鼓勵新的客戶移至 [https://visualstudio.microsoft.com/vs/pricing/](https://visualstudio.microsoft.com/vs/pricing/) 來探索 Visual Studio 的不同購買選項。

## <a name="other-questions"></a>其他問題

### <a name="q-can-i-use-the-monthly-azure-credits-as-a-visual-studio-subscriber-to-buy-more-visual-studio-cloud-subscriptions"></a>問：我可以使用 Visual Studio 訂用帳戶者身分的每月 Azure 點數來購買多個 Visual Studio 雲端訂用帳戶嗎？

答：不行，您不能使用 Visual Studio 訂用帳戶者身分的[每月 Azure 點數](https://azure.microsoft.com/pricing/member-offers/credit-for-visual-studio-subscribers/)來支付 Visual Studio Marketplace 購買。 任何 Visual Studio 雲端訂閱購買都會計入您的信用卡帳單。
進行採購之前，您必須[移除您的消費限制](https://azure.microsoft.com/pricing/spending-limits/)。

### <a name="q-whats-the-difference-between-annual-and-monthly-cloud-subscriptions"></a>問：雲端訂用帳戶的年度訂用帳戶和月租方案有何差異？

答：雲端訂用帳戶月租方案包含 Visual Studio 和 Azure DevOps Services 和 TFS 的使用。 年度雲端訂閱除此之外還包含訂閱者權益，包括使用 Windows 和其他 Microsoft 軟體來安裝和執行開發與測試，以及用於實驗 Azure 服務和執行雲端開發和測試、訓練、支援和其他更多作業的每月 Azure 點數。
[比較雲端訂閱權益和定價](https://visualstudio.microsoft.com/vs/pricing/)

### <a name="q-do-i-get-new-versions-of-visual-studio-if-i-buy-a-visual-studio-cloud-subscription"></a>問：如果購買 Visual Studio 雲端訂用帳戶是否可以取得新版本的 Visual Studio？

答：可以。 發行新版本時，您可以下載並執行它們。 而且您也可以繼續執行舊版。

### <a name="q-can-i-buy-visual-studio-cloud-subscriptions-from-my-software-reseller"></a>問：是否可以向軟體經銷商購買 Visual Studio 雲端訂用帳戶？

答：可以，如果您的經銷商參與雲端解決方案提供者 (CSP) 計畫。 詢問他們即可。

## <a name="buy-cloud-subscriptions-now"></a>立即購買雲端訂閱

* [Visual Studio Professional 月租方案](https://marketplace.visualstudio.com/items?itemName=ms.vs-professional-monthly)
* [Visual Studio Enterprise 月租方案](https://marketplace.visualstudio.com/items?itemName=ms.vs-enterprise-monthly)

## <a name="related-resources"></a>相關資源

* [Visual Studio 訂用帳戶系統管理入口網站](https://manage.visualstudio.com/)
* [Visual Studio 訂用帳戶支援](https://visualstudio.microsoft.com/vs/support/)
* [Visual Studio 雲端訂用帳戶購買 CSP](vscloud-csp.md)

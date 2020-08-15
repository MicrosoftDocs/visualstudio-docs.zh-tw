---
title: Microsoft Azure 權益 |Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 872c5746-5357-4764-949b-aa525a0adf1a
ms.date: 04/28/2020
ms.topic: how-to
description: 瞭解如何啟用 Visual Studio 訂用帳戶中所含的 Azure DevTest 個人點數權益。
ms.openlocfilehash: 276475393de374970685202079831bb06bedea6f
ms.sourcegitcommit: 577c905de52057a741e68c2ed168ea527813fda5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2020
ms.locfileid: "88247333"
---
# <a name="use-microsoft-azure-in-visual-studio-subscriptions"></a>在 Visual Studio 訂用帳戶中使用 Microsoft Azure
身為 Visual Studio 訂閱者，您不需要額外收費即可使用 Microsoft Azure。  有了 [每月 Azure DevTest 的個別點數](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/)，azure 就是您用於開發/測試的個人沙箱。  您可以佈建虛擬機器、雲端服務和其他 Azure 資源。  信用額度會依訂用帳戶層級而異。

## <a name="activation-steps"></a>啟用步驟
1. 登入 [https://my.visualstudio.com/benefits](https://my.visualstudio.com/benefits?wt.mc_id=o~msft~docs)。

2. 在 [權益] 頁面上的 [工具] 區段中找出 [Azure] 磚，然後選取權益磚底部的 [ **啟用** ] 連結。
   > [!div class="mx-imgBorder"]
   > ![Azure 磚](_img/vs-azure/vs-azure-tile.png)

3. 如果您沒有現有的 Azure 訂用帳戶，系統會要求您填入所需的資訊，以建立您的 Azure 訂用帳戶。  第一個步驟是提供您的個人資訊，然後選取 **[下一步]**。
   > [!div class="mx-imgBorder"]
   > ![Azure 註冊](_img/vs-azure/vs-azure-about-you.png)

4. 接下來，您必須使用簡單的驗證碼來驗證您的身分識別。 提供您的電話號碼，並選擇是否要以文字或電話接收程式碼。  輸入您收到的程式碼，然後選取 [ **驗證代碼**]。   
   > [!div class="mx-imgBorder"]
   > ![Azure 準備就緒](_img/vs-azure/vs-azure-identity.png)

5. 在最後一個步驟中，選取 [接受條款] 核取方塊，然後選取 [ **註冊**]。  就是這麼簡單！
   > [!div class="mx-imgBorder"]
   > ![Azure 準備就緒](_img/vs-azure/vs-azure-agreement.png)

0. 「Azure 儀表板快速入門中心」將會載入。  
   > [!div class="mx-imgBorder"]
   > ![Azure 儀表板](_img/vs-azure/vs-azure-quick-start.png) 

0. 將 [Azure 入口網站](https://portal.azure.com) 加入書簽，以便日後輕鬆存取。

## <a name="maintain-a-subscription-to-use-monthly-credits"></a>維護訂用帳戶以使用每月信用額度
如果您的 Visual Studio 訂用帳戶已過期或已移除，所有訂用帳戶權益（包括每月 Azure 開發/測試個別點數）都將無法再使用。 若要繼續使用 Azure 的每月信用額度，您必須更新訂用帳戶、購買新的訂用帳戶，或將 Azure 權益轉移至包含 Azure 開發/測試個人點數的有效訂用帳戶。  

> [!IMPORTANT]
> 您必須在目前的 Azure 訂用帳戶停用之前將資源轉移至另一個 Azure 訂用帳戶，否則將無法存取您的資料。  

有數種方式可以繼續使用 Azure 的每月信用額度。  若要儲存您的 Azure 資源，您必須將 [資源傳輸](https://docs.microsoft.com/azure/azure-resource-manager/management/move-resource-group-and-subscription) 至另一個 Azure 訂用帳戶，而不論您在下方選擇的動作為何。 

- **如果您直接購買 Visual Studio 訂**用帳戶，請透過 Microsoft Store 購買新的訂用帳戶或續訂您的訂用帳戶。  
    - [Visual Studio 企業版](https://www.microsoft.com/p/visual-studio-enterprise-subscription/dg7gmgf0dst4?activetab=pivot%3aoverviewtab)
    - [Visual Studio Professional](https://www.microsoft.com/p/visual-studio-professional-subscription/dg7gmgf0dst3?activetab=pivot%3aoverviewtab)
    - [Visual Studio Test Professional](https://www.microsoft.com/p/visual-studio-test-professional-subscription/dg7gmgf0dst6?activetab=pivot%3aoverviewtab)
- **如果您組織中的某人購買貴組織的訂用**帳戶，請 [洽詢您的 Visual Studio 訂閱管理員](https://docs.microsoft.com/visualstudio/subscriptions/contact-my-admin) ，並要求提供您所需的每月信用額度的訂閱。  
- 如果您在與另一個 Microsoft 帳戶相關聯的相同訂用帳戶層級上**有另一個**作用中的 Visual Studio 訂用帳戶，您可以在 Visual Studio 訂用帳戶[入口網站](https://my.visualstudio.com/subscriptions)中[新增其他帳戶](https://docs.microsoft.com/visualstudio/subscriptions/manage-vs-subscriptions#managing-my-profile)，以將 Azure 權益轉移至另一個有效的 Visual Studio 訂用  

請使用下方的資格表來判斷每個訂用帳戶類型包含多少信用額度。  


## <a name="convert-your-azure-subscription-to-pay-as-you-go"></a>將您的 Azure 訂用帳戶轉換為隨用隨付

如果您不再需要 Visual Studio 訂用帳戶或信用額度，但想要繼續使用您的 Azure 資源，請將 [您的資源轉移](https://docs.microsoft.com/azure/azure-resource-manager/management/move-resource-group-and-subscription) 至另一個 azure 訂用帳戶，或將您的 azure 訂用帳戶轉換為隨用隨付定價，方法是 [移除您的消費限制](https://docs.microsoft.com/azure/cost-management-billing/manage/spending-limit#remove-the-spending-limit-in-azure-portal)。 

如果您未採取其中一項動作，您的 Azure 訂用帳戶將會在收到電子郵件通知後的30天內停用並刪除。  

## <a name="have-a-question"></a>有任何疑問嗎?
如果您有關于傳輸資源、移除消費限制或其他 Azure 主題的問題，您可以在 Azure 入口網站中 [提交 Azure 支援要求](https://portal.azure.com/#blade/Microsoft_Azure_Support/HelpAndSupportBlade/overview) 。 

## <a name="eligibility"></a>資格
|                 訂用帳戶等級/方案                 |           優點           |                         可續約？                          |
|--------------------------------------------------------------|-----------------------------|-------------------------------------------------------------|
|              Visual Studio Enterprise Standard               |     每月信用點數 $150 美元     |                             是                             |
|              含 GitHub Enterprise 的 Visual Studio Enterprise               |     每月信用點數 $150 美元     |                             是                             |
|               Visual Studio Enterprise 每月               |        無法使用        |                                                             |
|             Visual Studio Professional Standard              |     每月信用點數 $50 美元      |                             是
|              含 GitHub Enterprise 的 Visual Studio Professional              |     每月信用點數 $150 美元     |                             是                             |
|              Visual Studio Professional 每月              |        無法使用        |                                                             |
|                    Visual Studio Test Pro                    |     每月信用點數 $50 美元      |                             是                             |
|                        MSDN 平台                        |     每月信用點數 $100 美元     |                             是                             |
|               Visual Studio Enterprise - NFR\*               |     每月信用點數 $150 美元     |                             是                             |
|                Visual Studio Enterprise - FTE                |     每月信用點數 $150 美元     |                             是                             |
|     Visual Studio Enterprise - Microsoft 合作夥伴網路     |     每月信用點數 $150 美元     |                             是                             |
|    Visual Studio Professional - Microsoft 合作夥伴網路    |        無法使用        |                                                             |
|        Visual Studio Enterprise – Imagine (Standard)         |        無法使用        |                                                             |
|         Visual Studio Enterprise – Imagine (Premium)         |        無法使用        |                                                             |
|             Visual Studio Enterprise – BizSpark              |     每月信用點數 $150 美元     |                             是                             |
|      Visual Studio Enterprise – MCT 軟體與服務      |     每月信用點數 $100 美元     |                             是                             |
| Visual Studio Enterprise – MCT 軟體與服務開發人員 |     每月信用點數 $150 美元     |                             是                             |

*包括禁止轉售 (NFR)、最有價值專家 (MVP)、區域經理 (RD)、Visual Studio 產業夥伴 (VSIP)

> [!NOTE]
> Microsoft 不再於雲端訂用帳戶中提供 Visual Studio Professional 年度訂用帳戶和 Visual Studio Enterprise 年度訂用帳戶。 現有的客戶體驗，以及更新、增加、減少或取消其訂用帳戶的能力將不會改變。 建議新客戶前往以 [https://visualstudio.microsoft.com/vs/pricing/](https://visualstudio.microsoft.com/vs/pricing/) 探索 Visual Studio 購買的不同選項。

不確定您使用哪一個訂用帳戶？  連接到 [https://my.visualstudio.com/subscriptions](https://my.visualstudio.com/subscriptions?wt.mc_id=o~msft~docs) 以查看指派給您的電子郵件地址的所有訂用帳戶。 若沒有看到您的所有訂用帳戶，可能有一或多個訂用帳戶是指派到不同的電子郵件地址。  您必須以該電子郵件地址登入才能查看對應的訂用帳戶。

## <a name="frequently-asked-questions"></a>常見問題集
### <a name="q-how-do-i-submit-a-technical-support-incident-from-within-the-azure-portal"></a>問：如何在 Azure 入口網站內提交技術支援事件？
答：從 Azure 入口網站內提交支援事件包含三個步驟。
1. 啟用您的技術支援權益，然後取得您的合約識別碼存取識別碼。
2. 將您的支援合約連結到您的 Azure 訂用帳戶。
3. 提交支援事件。

如需完整的詳細資料，請流覽 [技術支援](vs-tech-support.md) 檔。

### <a name="q-who-owns-the-intellectual-property-i-create-using-my-azure-devtest-individual-credit"></a>問：誰擁有我使用我的 Azure DevTest 個別點數所建立的智慧財產？
答：在該公司提供的資源上建立的智慧財產，就是提供資源之公司的智慧財產。 因此，如果您透過雇主收到您的 Visual Studio 訂用帳戶，則會套用其智慧財產原則。 

## <a name="support-resources"></a>支援資源
- 需要使用 Azure 的說明嗎？  請參閱下列資源：
  - 技術支援： [https://azure.microsoft.com/support/options/](https://azure.microsoft.com/support/options/)
  - [Azure 秘訣 & 訣竅](https://microsoft.github.io/AzureTipsAndTricks/ "Azure 秘訣 & 訣竅") 
- 如需 Visual Studio 訂閱的銷售、訂閱、帳戶和計費的協助，請聯絡 Visual Studio [訂閱支援](https://visualstudio.microsoft.com/subscriptions/support/)。
- 是否有關於 Visual Studio IDE、Azure DevOps Services 或其他 Visual Studio 產品或服務的問題？  前往 [Visual Studio 支援](https://visualstudio.microsoft.com/support/)

## <a name="see-also"></a>另請參閱
- [Visual Studio 檔](https://docs.microsoft.com/visualstudio/)
- [Azure DevOps 檔](https://docs.microsoft.com/azure/devops/)
- [Azure 檔](https://docs.microsoft.com/azure/)
- [Microsoft 365 檔](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>後續步驟
如需有關 Microsoft 工具與服務的詳細資訊，請參閱下列文件：
- [Azure](/azure/)
- [Azure DevOps](/azure/devops/)
- [Visual Studio IDE](/visualstudio/)

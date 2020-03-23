---
title: Microsoft 產品和服務合約 (MPSA) 中的 Visual Studio 訂閱 | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 03/03/2020
ms.topic: conceptual
description: Microsoft 產品和服務合約 (MPSA) 中的 Visual Studio 訂閱
ms.openlocfilehash: e4416bfab95bd7d1c38c392bfbf9efee9a06fc7f
ms.sourcegitcommit: f8e3715c64255b476520bfa9267ceaf766bde3b0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "78410250"
---
# <a name="visual-studio-subscriptions-in-a-microsoft-products-and-services-agreement-mpsa"></a>Microsoft 產品和服務合約 (MPSA) 中的 Visual Studio 訂閱
如果您已透過 MPSA 方案購買「Visual Studio 訂閱」，必須先了解幾個事項，才能成為 Visual Studio 訂閱系統管理員並將訂閱指派給您的使用者。 如果您已具備系統管理員身分，則可以直接前往 Visual Studio 訂閱[系統管理入口網站](https://manage.visualstudio.com/)。

MPSA 客戶現在可以在稱為[商務中心](https://businessaccount.microsoft.com/Customer)的新入口網站管理透過 MPSA 購買的資產，此中心支援一些與大量授權服務中心 (VLSC) 類似的功能。 其中包括查看許可證摘要、訂單、下載、金鑰、使用者等。但是，MPSA 中的視覺化工作室訂閱與雲服務的服務品質非常類似。 「商務中心」同樣使用「工作帳戶」來登入，而不是使用 Microsoft 帳戶 (MSA)。 如果組織使用 Office 365 或 Azure Active Directory 之類的雲端服務，而且您的電子郵件已是這兩項服務中任何一項的成員，則此電子郵件已經是「工作帳戶」。 這將可讓您使用現有密碼向「商務中心」註冊。 如果組織未使用雲端服務，而且您的電子郵件也不是「工作帳戶」，您可以使用它向「商務中心」註冊。

此外，在您成為 Visual Studio 訂閱系統管理員之後，將會在 Visual Studio 訂閱[系統管理入口網站](https://manage.visualstudio.com/)將訂閱指派給訂閱者。 在 MPSA 中，必須將 Visual Studio 訂閱佈建至它們個別的系統管理入口網站，亦即「Visual Studio 訂閱管理入口網站」。 若要這樣做，您必須將「購買帳戶」與租用戶 (亦即 contoso.onmicrosoft.com) 建立關聯。

請注意，有兩種類型的租用戶 (受控租用戶和非受控租用戶)。 受控租用戶係指已由組織內的系統管理員管理的租用戶。

非受控租用戶則是指未被指派任何系統管理員，因此無法用於 Office 365 這類線上服務的租用戶。 使用非「工作帳戶」的電子郵件向「商務中心」進行註冊時，也會建立非受控租用戶。 如果向「商務中心」進行註冊時，系統要求您建立密碼，即表示您的電子郵件不是「工作帳戶」，而所建立的即是非受控租用戶。

以下是在完成租用戶關聯程序之前，成為「Visual Studio 訂閱」系統管理員所需的幾個需求和步驟。

## <a name="pre-tenant-association-managed-tenant"></a>建立租用戶關聯之前 (受控租用戶)
- 您必須是「商務中心」的已註冊使用者。
- 您必須是所屬租用戶的「使用者管理員」(至少需具備此角色) 或「全域管理員」。 (這適用於公司已經使用「雲端服務」的情況)。 必須具備其中一個角色，才能成為 Visual Studio 訂閱系統管理員。
- 您必須是所屬租用戶中的「全域管理員」，才能將「購買帳戶」與租用戶建立關聯。
- 您必須是「商務中心」中的「帳戶管理員」(Account Admin) 或「帳戶管理員」(Account Manager)。
- [Azure](https://portal.azure.com/) 中您個人設定檔 (和任何其他使用者) 內的 [國家或地區] 欄位必須依據您的地區適當地填入資訊 (亦即 US、CA 等)。 

> [!NOTE]
> 任何您想要設定為 Visual Studio 訂閱系統管理員的使用者都不一定要是「商務中心」中的使用者，因為他們只需要符合準則 2 和 5 即可。

在您符合上述準則之後，即可依照下面的步驟繼續將「購買帳戶」與租用戶建立關聯。
1. 登入[商務中心](https://businessaccount.microsoft.com/Customer)。
2. 按一下 [帳戶]**** 索引標籤，然後選擇 [建立網域關聯]****。
3. 選取您的 [購買帳戶]**** (如果您有多個)。
4. 選取您的**租用戶** (亦即 contoso.onmicrosoft.com)。
5. 按一下 [建立網域關聯]****。

建立關聯時，所有符合準則的使用者通常在幾分鐘內就會佈建成 Visual Studio 訂閱系統管理員。 不過，有時可能會花費長達 24 小時的時間。 您的租用戶佈建完成之後，您將能夠存取「Visual Studio 訂閱系統管理入口網站」。 如果時間超過 24 小時，請使用以下步驟聯繫 MPSA 支援部門：
1. 連接到https://www.microsoft.com/licensing/mpsa/default
2. 按一下頁面頂部的 **"更多**"功能表。 
3. 選擇**支援**
4. 選擇**許可支援**
5. 選擇最適合您需求的支援選項。 

> [!NOTE]
> 如果在建立關聯之後，有符合步驟 2 和 5 的新使用者，您必須連絡 MPSA 支援服務。 MPSA 支援服務將會提供協助來佈建新的「Visual Studio 訂閱」系統管理員。

## <a name="tenant-association-unmanaged"></a>建立租用戶關聯 (非受控)
如果您已如上面所述，使用非「工作帳戶」(未在 Azure Active Directory “Azure AD” 中註冊) 的電子郵件向「商務中心」進行註冊，租用戶關聯將會有些微不同。 您將需要執行所謂的「網域接管」程序。 進行此程序時，您將使自己成為「全域管理員」，這會將您的租用戶從非受控變更為受控。

如需此程序的更詳細說明，您可以使用[快速入門指南](https://www.microsoft.com/Licensing/existing-customer/business-center-training-and-resources.aspx)。 請下載名為《設定及使用您的線上服務》** 的指南，此指南將會引導您逐步完成網域接管程序。 完成此程序之後，您的「購買帳戶」就也會與您的租用戶建立關聯。

> [!NOTE]
> 完成網域接管程序之後，您必須遵守＜建立租用戶關聯之前 (受控租用戶)＞一節中五個步驟的準則。 一旦符合這些準則，就只有要佈建額外的 Visual Studio 訂閱系統管理員時，才需要連絡 MPSA 支援服務。

## <a name="see-also"></a>另請參閱
- [視覺化工作室文檔](https://docs.microsoft.com/visualstudio/)
- [Azure 開發人員文檔](https://docs.microsoft.com/azure/devops/)
- [Azure 文件](https://docs.microsoft.com/azure/)
- [微軟 365 文檔](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>後續步驟
詳細瞭解如何管理視覺化工作室訂閱。
- [分配單個訂閱](assign-license.md)
- [分配多個訂閱](assign-license-bulk.md)
- [編輯訂閱](edit-license.md)
- [刪除訂閱](delete-license.md)
- [確定最大使用量](maximum-usage.md)

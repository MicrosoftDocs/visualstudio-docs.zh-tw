---
title: Microsoft 產品和服務合約 (MPSA) 中的 Visual Studio 訂閱 | Microsoft Docs
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 03/14/2018
ms.topic: conceptual
description: Microsoft 產品和服務合約 (MPSA) 中的 Visual Studio 訂閱
searchscope: VS Subscription
ms.openlocfilehash: cf0a6c0c7f09cefa70edd0af1dcedf46afdf81bf
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63002318"
---
# <a name="visual-studio-subscriptions-in-a-microsoft-products-and-services-agreement-mpsa"></a>Microsoft 產品和服務合約 (MPSA) 中的 Visual Studio 訂閱

如果您已透過 MPSA 方案購買「Visual Studio 訂閱」，必須先了解幾個事項，才能成為 Visual Studio 訂閱系統管理員並將訂閱指派給您的使用者。 如果您已具備系統管理員身分，則可以直接前往 Visual Studio 訂閱[系統管理入口網站](https://manage.visualstudio.com/)。

當您成為 MPSA 客戶時，系統會介紹一個入口網站，可供您管理透過 MPSA 購買的資產。 這個新的入口網站稱為[商務中心](https://businessaccount.microsoft.com/)，此中心支援一些就像「大量授權服務中心」(VLSC) 一樣的相同或新功能。 這些包括檢視您的「授權摘要」、「訂單」、「下載」、「金鑰」、「使用者」等。不過，MPSA 中 Visual Studio 訂閱的行為更像「雲端服務」。 「商務中心」同樣使用「工作帳戶」來登入，而不是使用「Microsoft 帳戶」。 如果組織使用 Office 365 或 Azure Active Directory 之類的雲端服務，而且您的電子郵件已是這兩項服務中任何一項的成員，則此電子郵件已經是「工作帳戶」。 這將可讓您使用組織指派給您的現有密碼來向「商務中心」註冊。 如果組織未使用雲端服務，而且您的電子郵件也不是「工作帳戶」，請勿擔心，因為您將使用它向「商務中心」註冊。

此外，在您成為 Visual Studio 系統管理員之後，將會在 Visual Studio 訂閱[系統管理入口網站](https://manage.visualstudio.com/)將訂閱指派給訂閱者。 在 MPSA 中，必須將 Visual Studio 訂閱佈建至其個別的管理入口網站，亦即「Visual Studio 訂閱系統管理入口網站」。 若要這樣做，您必須將「購買帳戶」與租用戶 (亦即 contoso.onmicrosoft.com) 建立關聯。

請注意，有兩種類型的租用戶 (受控租用戶和非受控租用戶)。 受控租用戶係指已由組織在其中以系統管理員身分管理的租用戶。

非受控租用戶則是當中沒有任何系統管理員而無法用於 Office 365 這類線上服務的租用戶。 使用非「工作帳戶」的電子郵件向「商務中心」進行註冊時，也會建立非受控租用戶。 如果向「商務中心」進行註冊時，系統要求您建立密碼，即表示您的電子郵件不是「工作帳戶」，而所建立的即是非受控租用戶。

在完成租用戶關聯程序之前，以下是成為「Visual Studio 訂閱」系統管理員所需的幾個需求和步驟。

## <a name="pre-tenant-association-managed-tenant"></a>建立租用戶關聯之前 (受控租用戶)

- 您必須是「商務中心」的已註冊使用者。
- 您必須是所屬租用戶的「使用者管理員」(至少需具備此角色) 或「全域管理員」。 (這適用於公司已經使用「雲端服務」的情況)。 必須具備其中一個角色，才能成為 Visual Studio 訂閱系統管理員。
- 您必須是所屬租用戶中的「全域管理員」，才能將「購買帳戶」與租用戶建立關聯。
- 您必須是「商務中心」中的「帳戶管理員」(Account Admin) 或「帳戶管理員」(Account Manager)。
- [Azure](https://portal.azure.com/) 中您個人設定檔 (和任何其他使用者) 內的 [國家或地區] 欄位必須依據您的地區適當地填入資訊 (亦即 US、CA 等)。 

> [!NOTE]
> 任何您想要設定為 Visual Studio 訂閱系統管理員的使用者都不一定要是「商務中心」中的使用者，因為他們只需要符合步驟 2 和 5 中的準則即可。

在您符合上述 5 個步驟中的準則之後，即可依照下面的步驟繼續將「購買帳戶」與租用戶建立關聯。
1. 登入[商務中心](https://businessaccount.microsoft.com/)。
2. 按一下 [帳戶] 索引標籤，然後選擇 [建立網域關聯]。
3. 選取您的 [購買帳戶] (如果您有多個)。
4. 選取您的**租用戶** (亦即 contoso.onmicrosoft.com)。
5. 按一下 [建立網域關聯]。

建立關聯時，所有符合所需準則的使用者通常在幾分鐘內就會佈建成 Visual Studio 訂閱系統管理員。 不過，有時可能會花費長達 24 小時的時間。 佈建完成之後，您將能夠存取「Visual Studio 訂閱系統管理入口網站」。 如果費時超過 24 小時，請連絡 MPSA 支援服務。

> [!NOTE]
> 如果在建立關聯之後，有符合步驟 2 和 5 的新使用者，您必須連絡 MPSA 支援服務。 MPSA 支援服務將會提供協助來佈建新的「Visual Studio 訂閱」系統管理員。

## <a name="tenant-association-unmanaged"></a>建立租用戶關聯 (非受控)

如果您已如上述第 5 個段落中所述，使用非「工作帳戶」(未在 Azure Active Directory “Azure AD” 中註冊) 的電子郵件向「商務中心」進行註冊，租用戶關聯將會有些微不同。 您將需要執行所謂的「網域接管」程序。 進行此程序時，您將使自己成為「全域管理員」，這會將您的租用戶從非受控變更為受控。

如需此程序的更詳細說明，您可以使用[快速入門指南](https://www.microsoft.com/en-us/Licensing/existing-customer/business-center-training-and-resources.aspx)。 請下載名為《設定及使用您的線上服務》的指南，此指南將會引導您逐步完成網域接管程序。 完成此程序之後，您的「購買帳戶」就也會與您的租用戶建立關聯。

> [!NOTE]
> 完成網域接管程序之後，您必須遵守＜建立租用戶關聯之前 (受控租用戶)＞一節中五個步驟的準則。 一旦符合這些準則，就只有要佈建額外的 Visual Studio 訂閱系統管理員時，才需要連絡 MPSA 支援服務。

如果您需要協助或有任何問題，可以透過電話或電子郵件來連絡支援人員。

MPSA 支援：**1-866-200-9611**，服務時間為太平洋時間星期一到星期五上午 5:30 到下午 5:30

電子郵件：ngvlsup@microsoft.com

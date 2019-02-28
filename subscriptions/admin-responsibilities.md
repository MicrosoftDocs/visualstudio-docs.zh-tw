---
title: 系統管理員責任 | Visual Studio Marketplace
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 03/13/2018
ms.topic: conceptual
description: 了解訂用帳戶系統管理員的責任。
searchscope: VS Subscription
ms.openlocfilehash: ca1dc2dd7a2232a85a7e6aefece63272bb0039fc
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/26/2019
ms.locfileid: "56842347"
---
# <a name="overview-of-administrator-responsibilities"></a>系統管理員責任概觀
身為系統管理員，您可以管理組織的訂用帳戶。  系統管理員角色也有責任確保訂用帳戶根據授權條款進行管理。 本文章概述系統管理員角色的責任、權益和限制。

## <a name="roles--responsibilities"></a>角色與責任
Visual Studio 系統管理員具有四項重要的責任：
1.  **了解 Visual Studio 訂用帳戶的權益和限制。** 正確了解您的權益，可讓您使用雲端服務減少硬體成本，並減少生產前環境的每個使用者授權的軟體成本。
2.  **將 Visual Studio 訂用帳戶指派給特定的具名個人，並且鼓勵大家使用。** 您的合約要求將 Visual Studio 訂用帳戶指派給特定的具名個人。 請追蹤您所指派的個人，確保他們可存取並充分利用其 Visual Studio 訂用帳戶中所包含的權益。
3.  **正確清查生產前環境。** 若要確保與 Visual Studio 授權軟體互動的所有使用者都已使用他們自己的 Visual Studio 訂用帳戶取得適當的授權，這是不可或缺的作業。
4.  **根據時間表追蹤使用者指派變更，並取得的額外授權。** Microsoft 大量授權 (VL) 合約和 MPSA 可讓您靈活地使用及指派 Visual Studio 訂用帳戶。 相對地，您應該根據協議中所述的時間表追蹤軟體使用和使用者指派的變更，並下單取得額外的授權。

## <a name="benefits-and-limitations"></a>權益與限制
Visual Studio 訂用帳戶允許開發小組成員安裝和使用軟體來設計、開發、測試、評估及示範其他軟體。 Visual Studio 訂用帳戶軟體未授權用於生產環境。

|                                          |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 依使用者授權                     | MSDN 平台和所有層級的 Visual Studio 訂用帳戶都是以每個使用者為基礎來授權。 要與這些產品和服務隨附的軟體互動 (安裝、設定或存取) 的每個開發小組成員，都必須有自己的 Visual Studio 訂用帳戶。                                                                                                                                                                                                                                                                                                                                  |
| 無限制安裝                  | 每個授權的使用者可以在任意數目的裝置上安裝和使用軟體，來設計、開發、測試、評估及示範軟體。 例外情況是 Microsoft Office，僅提供一部桌上型電腦的授權。 您可以在公司、住家、學校，以及客戶辦事處的裝置或協力廠商所裝載的專用硬體上安裝及使用 Visual Studio 授權的軟體。                                                                                                                                                                                                                                  |
| 不適用於生產環境 | Visual Studio 訂用帳戶軟體未授權用於生產環境，包括終端使用者存取但用於接受度測試或意見反應以外用途的任何環境、連線到生產資料庫的環境、支援災害復原或生產環境備份的環境，或在活動尖峰期間用於生產的環境。 此項目的例外狀況包含 [Visual Studio Licensing White Paper](https://aka.ms/vslicensing) (Visual Studio 授權白皮書) 中所述之某些訂用帳戶層級的特殊權益。                                                                                            |
| 授權重新指派                     | 當使用者離開小組而不再需要授權時，您可以在過了 90 天後重新指派授權。 當您重新指派授權時，仍然提供已使用的任何產品金鑰，但將不會被取代。 針對擁有 Enterprise 合約 (EA) 的組織，原始使用者曾使用的任何權益 (例如 Pluralsight 訓練) 都會被重設。                                                                                                                                                                                                                                                 |
| 終端使用者的例外狀況                  | 在軟體開發專案結束時，終端使用者通常會審核應用程式，並判斷它是否符合發行的必要準則。 此程序稱為使用者接受度測試 (UAT)。 企業贊助商或產品經理等小組成員可作為終端使用者的代理人。 如果以其他方式使用軟體符合所有的 Visual Studio 授權條款，則沒有 Visual Studio 訂用帳戶的終端使用者也可以存取軟體來進行 UAT。 其主要角色為設計、開發或測試軟體的人員很少有資格同時成為「終端使用者」。 |

## <a name="inventory-of-pre-production-environment"></a>清查生產前環境
Visual Studio 訂用帳戶透過計算使用者　(而不是裝置) 來簡化資產管理。

Visual Studio 系統管理員必須將 Visual Studio 訂用帳戶指派給**特定的指定個人**。 **不允許**使用 Dev1、Dev2 或 Dev3 等命名慣例。

以下是用來簡化生產前環境清查作業的一些方法：
- 檢閱您的使用者指派。 Microsoft 提供一個稱為 [Visual Studio 系統管理入口網站](https://manage.visualstudio.com/)的網站，協助您追蹤 Visual Studio 訂用帳戶指派。
- 使用內部部署或雲端式 Active Directory 來列出使用者。 如果您使用 Active Directory 來管理使用者存取權，則可以透過其目錄的成員資格來識別開發及測試使用者。
- 使用自動化工具來清查系統。 您可能也需要使用軟體清查工具來協助管理軟體資產，以及區分生產前環境與生產環境。 使用 Microsoft System Center 的許多客戶都會建立命名慣例，以協助將清查程序的這個部分自動化。
- 取得手動重新調解的協助。 登錄您的員工，協助協調開發和測試使用者與開發和測試環境。

## <a name="large-teams-and-external-contractors"></a>大型小組和外部承攬人
Visual Studio 訂用帳戶系統管理員必須負責確保與 Visual Studio 授權軟體進行互動的每個使用者，已使用自己的 Visual Studio 訂用帳戶取得適當的授權。

### <a name="internal-teams"></a>內部小組
現代軟體組織通常包含來自數個群組的專案關係人。 請識別每個群組中可以協助您追蹤使用者清查和變更的連絡人。
每個組織都不同，但參與開發的典型小組清單可能包含：
- 軟體工程小組。
- 業務小組，包括產品擁有者和商務分析師。
- 專案管理小組。
- 品質小組，包括 QA 員工和手動測試人員。
- IT 營運，包括生產前和實驗室基礎結構管理員。

### <a name="external-contractors-and-partners"></a>外部承包商和合作夥伴
外部承包商可能會攜帶授權來參與 Visual Studio 授權環境。 Microsoft 認證合作夥伴可能會收到一些免費的 Visual Studio 訂用帳戶供其內部使用。 不過，這些訂用帳戶未涵蓋產生營收的活動，例如為客戶開發自訂軟體。 請要求合作夥伴將認證信函傳送給您，其中說明他們所提供的授權以及他們需要您購買的授權。

## <a name="track-user-assignment-and-process-orders"></a>追蹤使用者指派和處理訂單
Visual Studio 訂用帳戶系統管理員應該要根據大量授權合約或 Microsoft 產品和服務合約中所述的時間表，追蹤 Visual Studio 使用量，並處理任何使用量增加而產生的訂單。 新的 Visual Studio 訂用帳戶系統管理入口網站提供可顯示可用和已使用之授權的實用追蹤器，進而簡化了此作業。

### <a name="high-water-mark-of-usage"></a>使用量的上限標準
**在下列情況下，貴公司購買 Visual Studio 訂用帳戶的義務會立即生效：**
- 已將授權指派給使用者。
- 使用者會與 Visual Studio 軟體互動。

採購義務完成與否取決於**使用量的上限標準**。 此上限標準是每日的使用者指派或與 Visual Studio 軟體互動的使用者所產生的用量，以較高者為準。
1.  Visual Studio 訂用帳戶系統管理員可以將 Visual Studio 訂用帳戶指派給個人，藉以提高使用量高水位線。
2.  如果從原始指派以來已經過 90 天，Visual Studio 訂用帳戶系統管理員就可以將某個訂閱者的訂用帳戶重新指派給另一個訂閱者。 若要避免虛高的上限標準，請務必要先移除現有的訂用帳戶，再新增新的訂用帳戶。
3.  Visual Studio 訂用帳戶系統管理員可能會變更個人的指派訂用帳戶層級，這會造成某個指派的用量降低，而另一個指派的用量增加。 當您降低某個訂閱者的指派訂用帳戶層級時，該人員必須立即停止使用並解除安裝只能在較高層級的訂用帳戶中使用的任何項目。

### <a name="cloud-subscriptions-open-license-or-open-value"></a>雲端訂用帳戶，Open License 或 Open Value
您可能會透過方案 (例如 Microsoft Cloud 訂用帳戶、Open Licens 或 Open Value) 獲得訂用帳戶的指派。 如果是這樣，您必須在使用者 (員工或外部承包商) 開始與 Visual Studio 授權軟體進行互動的當月內處理額外使用者的訂單。

### <a name="enterprise-mpsa-and-select-agreements"></a>Enterprise、MPSA 和 Select 合約
Microsoft Enterprise 合約 (EA)、MPSA 及 Select Plus 合約可讓您隨著時間變化，靈活使用 Visual Studio 軟體並進行授權。 Visual Studio 系統管理員必須發出年度較正訂單，使其軟體授權數量能夠符合合約期間所產生之使用量的上限標準。
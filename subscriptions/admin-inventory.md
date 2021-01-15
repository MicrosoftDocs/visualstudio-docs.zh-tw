---
title: Visual Studio 訂用帳戶中的生產前清查 |Visual Studio Marketplace
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: 7d74e113-8fb2-490e-8502-48cce7b1327a
ms.date: 01/14/2021
ms.topic: conceptual
description: 瞭解管理員負責執行生產前清查的責任
ms.openlocfilehash: abcb3c8c1213885b5e543b05cf912c418acaa3f5
ms.sourcegitcommit: 4ee20054afe7bcf5c0aed504dec01e18059fbbd0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/15/2021
ms.locfileid: "98226483"
---
# <a name="inventory-of-pre-production-environment"></a>清查生產前環境
Visual Studio 訂用帳戶透過計算使用者　(而不是裝置) 來簡化資產管理。

Visual Studio 系統管理員必須將 Visual Studio 訂閱指派給 **特定的命名個人**。 **不允許** 像是 Dev1、Dev2 或使用小組名稱 (例如 "FeatureTeam") 的命名慣例。

以下是用來簡化生產前環境清查作業的一些方法：
- 檢閱您的使用者指派。 Microsoft 提供一個稱為 [Visual Studio 系統管理入口網站](https://manage.visualstudio.com/)的網站，協助您追蹤 Visual Studio 訂用帳戶指派。
- 使用內部部署或雲端式 Active Directory 來列出使用者。 如果您使用 Active Directory 來管理使用者存取權，則可以透過其目錄的成員資格來識別開發及測試使用者。
- 使用自動化工具來清查系統。 您可能也需要使用軟體清查工具來協助管理軟體資產，以及區分生產前環境與生產環境。 使用 Microsoft System Center 的許多客戶都會建立命名慣例，以協助將清查程序的這個部分自動化。
- 取得手動重新調解的協助。 登錄您的員工，協助協調開發和測試使用者與開發和測試環境。

> [!NOTE]
> Visual Studio 訂用帳戶軟體未授權用於生產環境，包括終端使用者存取但用於接受度測試或意見反應以外用途的任何環境、連線到生產資料庫的環境、支援災害復原或生產環境備份的環境，或在活動尖峰期間用於生產的環境。 此項目的例外狀況包含 [Visual Studio Licensing White Paper](https://aka.ms/vslicensing) (Visual Studio 授權白皮書) 中所述之某些訂用帳戶層級的特殊權益。  

## <a name="resources"></a>資源
- [Visual Studio 授權技術白皮書](https://visualstudio.microsoft.com/wp-content/uploads/2019/06/Visual-Studio-Licensing-Whitepaper-May-2019.pdf)
- [Visual Studio 管理與訂閱支援](https://visualstudio.microsoft.com/support/support-overview-vs)
- [大量授權條款](https://www.microsoft.com/licensing/product-licensing/products.aspx)

## <a name="see-also"></a>請參閱
- [Visual Studio 檔](/visualstudio/)
- [Azure DevOps 文件](/azure/devops/) \(英文\)
- [Azure 檔](/azure/)
- [Microsoft 365 檔](/microsoft-365/)

## <a name="next-steps"></a>後續步驟
深入瞭解系統管理員的責任：
- [系統管理員責任](admin-responsibilities.md)
- [管理大型小組及外部承攬人](manage-teams.md)
- [追蹤使用者指派及處理訂單](assignments-orders.md)
- 使用[使用量上限](maximum-usage.md)來追蹤購買承諾用量
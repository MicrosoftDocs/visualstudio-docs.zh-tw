---
title: 清查生產前環境 | Visual Studio Marketplace
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 7d74e113-8fb2-490e-8502-48cce7b1327a
ms.date: 03/06/2020
ms.topic: conceptual
description: 了解系統管理員要進行生產前清查的責任
ms.openlocfilehash: dc307d9d2f83666c6648a35b3e28a81da2de5c38
ms.sourcegitcommit: eeff6f675e7850e718911647343c5df642063d5e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2020
ms.locfileid: "80232763"
---
# <a name="inventory-of-pre-production-environment"></a>清查生產前環境
Visual Studio 訂用帳戶透過計算使用者　(而不是裝置) 來簡化資產管理。

Visual Studio 系統管理員必須將 Visual Studio 訂用帳戶指派給**特定的指定個人**。 **不允許**像是 Dev1、Dev2 或使用小組名稱 (例如 "FeatureTeam") 的命名慣例。

以下是用來簡化生產前環境清查作業的一些方法：
- 檢閱您的使用者指派。 Microsoft 提供一個稱為 [Visual Studio 系統管理入口網站](https://manage.visualstudio.com/)的網站，協助您追蹤 Visual Studio 訂用帳戶指派。
- 使用內部部署或雲端式 Active Directory 來列出使用者。 如果您使用 Active Directory 來管理使用者存取權，則可以透過其目錄的成員資格來識別開發及測試使用者。
- 使用自動化工具來清查系統。 您可能也需要使用軟體清查工具來協助管理軟體資產，以及區分生產前環境與生產環境。 使用 Microsoft System Center 的許多客戶都會建立命名慣例，以協助將清查程序的這個部分自動化。
- 取得手動重新調解的協助。 登錄您的員工，協助協調開發和測試使用者與開發和測試環境。

## <a name="resources"></a>資源
- [視覺工作室許可白皮書](https://visualstudio.microsoft.com/wp-content/uploads/2019/06/Visual-Studio-Licensing-Whitepaper-May-2019.pdf)
- [Visual Studio 管理與訂閱支援](https://visualstudio.microsoft.com/support/support-overview-vs)
- [大量授權條款](https://www.microsoft.com/licensing/product-licensing/products.aspx)

## <a name="see-also"></a>另請參閱
- [視覺化工作室文檔](https://docs.microsoft.com/visualstudio/)
- [Azure 開發人員文檔](https://docs.microsoft.com/azure/devops/)
- [Azure 文件](https://docs.microsoft.com/azure/)
- [微軟 365 文檔](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>後續步驟
深入了解系統管理員的責任：
- [系統管理員責任](admin-responsibilities.md)
- [管理大型小組及外部承攬人](manage-teams.md)
- [追蹤使用者指派和處理訂單](assignments-orders.md)
- 使用[使用量上限](maximum-usage.md)來追蹤購買承諾用量




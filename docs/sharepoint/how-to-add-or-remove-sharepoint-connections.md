---
title: 如何：加入或移除 SharePoint 連接 |Microsoft Docs
description: 在 Visual Studio 的伺服器總管視窗中，使用 [SharePoint 連接] 節點來新增或移除 SharePoint 連接。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, browsing SharePoint sites
- SharePoint development in Visual Studio, SharePoint Connections
- SharePoint Connections [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 57ff132274ba7f720a845078b0424fe235d9c31e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99923450"
---
# <a name="how-to-add-or-remove-sharepoint-connections"></a>如何：加入或移除 SharePoint 連接
  伺服器總管可讓您流覽 SharePoint 網站以及資料連線。 不過，您必須先將 SharePoint 網站的內容新增至 **sharepoint [連接** ] 節點，才能流覽 sharepoint 網站的內容。

### <a name="to-add-a-sharepoint-site-to-the-sharepoint-connections-node"></a>將 SharePoint 網站加入至 SharePoint 連接節點

1. 在功能表列上，選擇 [ **View**]、[ **伺服器總管**]。

2. 在 [**伺服器總管** 中，選擇 [ **SharePoint 連接**] 節點，然後在功能表列上選擇 [**工具**  >  **加入 sharepoint 連接**]。

3. 在 [ **加入 Sharepoint 連接** ] 方塊中，輸入 [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] SharePoint 網站的 (例如， http://testserver/sites/unittests) 。

### <a name="to-delete-a-sharepoint-site-from-the-sharepoint-connections-node"></a>從 SharePoint 連接節點刪除 SharePoint 網站

1. 在功能表列上，選擇 [ **View**]、 **伺服器總管** 以開啟 **伺服器總管**。

2. 展開 [ **Sharepoint 連接** ] 節點，以顯示您想要從 **伺服器總管** 中刪除的 sharepoint 網站。

3. 選擇網站，然後在功能表列上選擇 [**編輯**  >  **刪除**]。

    > [!NOTE]
    > 此步驟不會刪除基礎網站;它只會刪除 **伺服器總管** 的連接。

## <a name="see-also"></a>另請參閱
- [使用伺服器總管流覽 SharePoint 連接](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)

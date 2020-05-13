---
title: 樣本策略與屬性視窗 :微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, template policy
ms.assetid: 1d8019d3-5e57-47ba-b358-526b0796a63b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 08ed6f416441d06767661e63b5e32454dbe07f93
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704671"
---
# <a name="template-policy-and-the-properties-window"></a>範本原則和屬性視窗
當專案包含在企業範本專案中時,該企業範本專案可以強制執行策略。 範本策略成為約束系統,可用於設置屬性的預設值、隱藏屬性、添加屬性等。

 使用範本策略來控制**屬性視窗中資訊**的顯示與<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>實現 不同。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>在元件級別處理物件屬性,而範本策略可用於在解決方案或專案級別約束物件屬性。 換句話說

- 實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>方法,以確定特定物件的**屬性「 視窗中**顯示 」

- 在解決方案與專案等級使用樣本政策來決定指定物件的**屬性屬性「 視窗中**顯示 」 的內容

  在**解決方案資源管理員**中選擇指定類型的專案項時,使用範本策略有選擇地約束**屬性**視窗中的特定屬性,這對處理專案的開發團隊的所有成員都是有益的。 例如,使用範本策略,可以為開發人員設置資料庫中的所有連接字串資訊,並使連接字串為唯讀。 通過這種方式,您可以提供一種簡單的方法來確保每個開發人員使用正確的路徑進行數據訪問。

## <a name="see-also"></a>另請參閱
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>
- [擴充屬性](../../extensibility/internals/extending-properties.md)

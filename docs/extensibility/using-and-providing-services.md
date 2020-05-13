---
title: 使用和提供服務 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- examples [Visual Studio SDK], services
- Visual Studio, services
- services
ms.assetid: c0b415ba-b825-4da0-9faf-8a60a663e302
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8741d8d66af96ad4c6abea44b238393a34c5aa95
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698731"
---
# <a name="using-and-providing-services"></a>使用和提供服務
服務是兩個 VSPackages 之間的協定。 一個 VSPackage 提供了一組特定的介面,供另一個 VSPackage 使用。 例如,[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]<xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog>向 它載入的任何 VSPackage 提供服務。 此服務提供<xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>介面,該介面可用於寫入活動日誌。 有關詳細資訊,請參閱[:使用活動紀錄](../extensibility/how-to-use-the-activity-log.md)。

 VSPackages 可以<xref:Microsoft.VisualStudio.Shell.Interop.IProfferService>使用 介面提供自己的服務。

 Visual Studio 提供重要的服務,例如:

|IDE 服務|描述|
|-----------------|-----------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>|提供對處理基本功能、VS 包和註冊表的 IDE 服務的訪問。|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|在 IDE 中提供基本視窗和與 UI 相關的功能,例如創建工具和文件視窗的功能。|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|提供與解決方案相關的基本功能,例如枚舉專案、創建新專案和監視專案更改的能力。|

## <a name="in-this-section"></a>本節內容
- [服務要點](../extensibility/internals/service-essentials.md)呈現視覺工作室服務的重要元素。

- [如何:取得服務](../extensibility/how-to-get-a-service.md)討論如何請求(使用)服務。

- [如何:提供服務](../extensibility/how-to-provide-a-service.md)討論如何提供服務。

- [如何:提供異步視覺工作室服務](../extensibility/how-to-provide-an-asynchronous-visual-studio-service.md)討論如何提供異步服務。

- [如何:故障排除服務](../extensibility/how-to-troubleshoot-services.md)討論常見問題並提出解決方案。

## <a name="related-sections"></a>相關章節
- [視覺化工作室 SDK](../extensibility/visual-studio-sdk.md)

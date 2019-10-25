---
title: 範本原則和 [屬性] 視窗 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, template policy
ms.assetid: 1d8019d3-5e57-47ba-b358-526b0796a63b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e7135a7c99f1566eaacb4079e9787cf2b5606682
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72722684"
---
# <a name="template-policy-and-the-properties-window"></a>範本原則和屬性視窗
當專案包含在企業範本專案中時，該企業範本專案可以強制執行原則。 範本原則會成為條件約束系統，可用來設定屬性的預設值、隱藏屬性、加入屬性等等。

 使用範本原則控制 [**屬性**] 視窗中的資訊顯示，與執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> 不同。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> 會在元件層級處理物件屬性，而範本原則則可以用來限制方案或專案層級的物件屬性。 換句話說

- 在 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> 上執行方法，以判斷在特定物件的 [**屬性**] 視窗中顯示的內容

- 在方案和專案層級使用範本原則，以判斷在先前指定物件的 [**屬性**] 視窗中顯示的內容

  當在**方案總管**中選取所指定類型的專案專案時，使用範本原則選擇性地限制 [**屬性**] 視窗中的特定屬性，對於開發小組處理專案的所有成員都很有説明。 例如，您可以使用範本原則，為開發人員設定資料庫中的所有連接字串資訊，並將連接字串設為唯讀。 如此一來，您就可以提供簡單的方法，確保每個開發人員都使用正確的資料存取路徑。

## <a name="see-also"></a>請參閱
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>
- [擴充屬性](../../extensibility/internals/extending-properties.md)
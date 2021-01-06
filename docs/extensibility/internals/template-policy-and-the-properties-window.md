---
title: 範本原則和屬性視窗 |Microsoft Docs
description: 瞭解如何使用範本原則來設定屬性的預設值、隱藏屬性，以及在屬性視窗中新增屬性。
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 105a90699689ff6eab6ea5bdfa3d4037e700ecb5
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877711"
---
# <a name="template-policy-and-the-properties-window"></a>範本原則和屬性視窗
當專案包含在企業範本專案中時，該企業範本專案可以強制執行原則。 範本原則變成一種限制系統，可用來設定屬性的預設值、隱藏屬性、新增屬性等等。

 在 [ **屬性** ] 視窗中使用範本原則來控制資訊的顯示方式，不同于執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> 。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> 處理元件層級的物件屬性，而範本原則可以用來限制方案或專案層級的物件屬性。 換句話說

- 在上執行方法 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> ，以決定要在特定物件的 [ **屬性** ] 視窗中顯示的內容。

- 使用方案和專案層級的範本原則，判斷在先前指定之物件的 [ **屬性** ] 視窗中顯示的內容。

  在 **方案總管** 中選取指定類型的專案專案時，使用範本原則選擇性地限制 [**屬性**] 視窗中的特定屬性，對於處理專案的開發小組的所有成員都很有用。 例如，您可以使用範本原則，為開發人員設定資料庫中的所有連接字串資訊，並將連接字串設為唯讀。 如此一來，您就可以提供簡單的方法，以確保每位開發人員都使用正確的資料存取路徑。

## <a name="see-also"></a>請參閱
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>
- [擴充屬性](../../extensibility/internals/extending-properties.md)

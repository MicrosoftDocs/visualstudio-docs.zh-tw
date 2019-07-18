---
title: 組態和 SelectedItem 物件的自動化 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], SelectedItem object
- automation [Visual Studio SDK], builds
ms.assetid: 120377f1-51aa-4445-b2f7-06ab7fc2b47f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e6c9dc8012433f9ec73f15b9249f6b7ac08bdad7
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66347965"
---
# <a name="automation-for-configuration-and-selecteditem-objects"></a>組態和 SelectedItem 物件的自動化

您可以自動化組建和 Visual Studio 中的選取項目的程序。

## <a name="automation-for-builds"></a>組建的自動化

建置或設定具有您實作時，會提供 automation 模型<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider>。 如需詳細資訊，請參閱[了解組建組態](../../ide/understanding-build-configurations.md)。

如果您建立 VSPackage，而且想要控制組態選項，您必須使用 automation 模型。

## <a name="automation-for-selecteditem"></a>SelectedItem 自動化

您沒有提供實作`SelectedItem`物件，因為 Visual Studio 包含標準的實作。 不過，您可以實作`SelectedItem`如果您偏好的物件。 您必須實作物件，包含`SelectedItem`介面，並將回應傳回給呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>方法`VSITEMID`設定為[__VSHPROPID。VSHPROPID_ExtSelectedItem](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_ExtSelectedItem>)。

## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>
- [參與 automation 模型](../../extensibility/internals/contributing-to-the-automation-model.md)
- [了解建置組態](../../ide/understanding-build-configurations.md)
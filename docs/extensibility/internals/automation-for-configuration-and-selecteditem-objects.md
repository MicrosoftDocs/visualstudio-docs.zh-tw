---
title: Configuration 和 SelectedItem 物件的自動化 |Microsoft Docs
description: 瞭解如何使用 Shell Interop 中的設定和 SelectedItem 物件，將 Visual Studio 組建和選取的專案進程自動化。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], SelectedItem object
- automation [Visual Studio SDK], builds
ms.assetid: 120377f1-51aa-4445-b2f7-06ab7fc2b47f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9f6e7f153e7d5b32e54cc51e3b7af06f14545cea
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105086257"
---
# <a name="automation-for-configuration-and-selecteditem-objects"></a>Configuration 和 SelectedItem 物件的自動化

您可以將 Visual Studio 中的組建和選取的專案進程自動化。

## <a name="automation-for-builds"></a>組建的自動化

組建或設定具有可在您執行時提供的自動化模型 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider> 。 如需詳細資訊，請參閱[了解組建組態](../../ide/understanding-build-configurations.md)。

如果您建立 VSPackage 並想要控制設定選項，就必須使用 automation 模型。

## <a name="automation-for-selecteditem"></a>SelectedItem 自動化

您不需要提供物件的執行， `SelectedItem` 因為 Visual Studio 包含標準的執行。 但是，如果您想要的話，可以執行此 `SelectedItem` 物件。 您必須執行包含介面的物件 `SelectedItem` ，並將回應傳回至方法的呼叫，並 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> `VSITEMID` 將設定為 [__VSHPROPID。VSHPROPID_ExtSelectedItem](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_ExtSelectedItem>)。

## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>
- [參與 automation 模型](../../extensibility/internals/contributing-to-the-automation-model.md)
- [了解組建組態](../../ide/understanding-build-configurations.md)

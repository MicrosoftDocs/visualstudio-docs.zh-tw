---
title: 設定與選取項目物件的自動化 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], SelectedItem object
- automation [Visual Studio SDK], builds
ms.assetid: 120377f1-51aa-4445-b2f7-06ab7fc2b47f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0341cdf56b32b8b1ac77104b3f3e813ae0610767
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709964"
---
# <a name="automation-for-configuration-and-selecteditem-objects"></a>設定與選取項目的自動化

您可以在可視化工作室中自動執行生成和選定項目進程。

## <a name="automation-for-builds"></a>組建自動化

生成或配置具有實現<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider>時提供的自動化模型。 如需詳細資訊，請參閱[了解組建組態](../../ide/understanding-build-configurations.md)。

如果創建 VSPackage 並希望控制配置選項,則必須使用自動化模型。

## <a name="automation-for-selecteditem"></a>選取項目的自動化

您不必為物件提供實現,`SelectedItem`因為 Visual Studio 包含標準實現。 但是,如果您願意,`SelectedItem`可以實現該物件。 您必須實現包含介面的物件,`SelectedItem`並將<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>`VSITEMID`設定為__VSHPROPID的方法的呼叫回回應[。VSHPROPID_ExtSelectedItem](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_ExtSelectedItem>)。

## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>
- [為自動化模型做出貢獻](../../extensibility/internals/contributing-to-the-automation-model.md)
- [了解組建組態](../../ide/understanding-build-configurations.md)

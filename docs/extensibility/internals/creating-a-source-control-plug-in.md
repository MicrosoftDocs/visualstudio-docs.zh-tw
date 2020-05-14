---
title: 建立原始碼管理外掛程式 :微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- plug-ins, source control
- source control plug-ins
- source control [Visual Studio SDK], plug-ins
ms.assetid: c7e69fa4-150e-469a-a6fc-fa1260bdbb07
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9e0d9dc54a61cabe7bdd5c21c10abf0def34ff6a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709178"
---
# <a name="create-a-source-control-plug-in"></a>建立原始碼管理外掛程式
Visual Studio SDK 提供的資源使[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]您能夠向 整合式開發環境 (IDE) 添加原始碼管理功能。 它允許您使用任何符合本文件中概述的原始程式碼管理外掛程式 API 的外掛程式 DLL。

## <a name="in-this-section"></a>本節內容
- [開始使用](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)

 描述如何安裝原始碼管理外掛程式並突出顯示目前可用的原始程式碼管理外掛程式 API 版本。

- [架構](../../extensibility/internals/source-control-plug-in-architecture.md)

 使用體系結構圖來解釋原始程式碼管理外掛程式與IDE的[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]整合。

- [測試指南](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)

 提供有關如何測試原始程式碼管理外掛程式的安裝和操作的指導。

## <a name="related-sections"></a>相關章節
- [建立原始碼管理 VS 套件](../../extensibility/internals/creating-a-source-control-vspackage.md)

 討論如何建立原始碼管理 VSPackage,該原始程式碼管理不僅提供原始程式碼管理功能[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)],而且替換原始程式碼管理 UI。

- [原始程式管理外掛程式](../../extensibility/source-control-plug-ins.md)

 提供原始程式碼管理外掛程式 API 中所有元素的完整清單。

- [原始碼管理](../../extensibility/internals/source-control.md)

 討論了實現原始碼管理作為的整合功能的選項[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。

---
title: 建立原始檔控制外掛程式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- plug-ins, source control
- source control plug-ins
- source control [Visual Studio SDK], plug-ins
ms.assetid: c7e69fa4-150e-469a-a6fc-fa1260bdbb07
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c33b852a585825f3c5b5fc415b01ac31e35f763f
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56606521"
---
# <a name="create-a-source-control-plug-in"></a>建立原始檔控制外掛程式
Visual Studio SDK 提供的資源，可讓您將加入原始檔控制項功能，以[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]整合式的開發環境 (IDE)。 它可讓您使用這份文件中所述的原始檔控制外掛程式 API 使用任何符合的外掛程式 DLL。

## <a name="in-this-section"></a>本節內容
- [開始使用](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)

 描述如何安裝原始檔控制外掛程式，並反白顯示目前可用的原始檔控制外掛程式 API 版本。

- [架構](../../extensibility/internals/source-control-plug-in-architecture.md)

 使用架構圖說明的原始檔控制外掛程式整合[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE。

- [測試指南](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)

 提供有關如何安裝及操作的原始檔控制外掛程式測試的指引。

## <a name="related-sections"></a>相關章節
- [建立原始檔控制 VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md)

 討論如何建立原始檔控制 VSPackage，不僅提供原始檔控制功能，但會取代[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]原始檔控制 UI。

- [原始檔控制外掛程式](../../extensibility/source-control-plug-ins.md)

 提供原始檔控制外掛程式 API 中的所有項目的完整清單。

- [原始檔控制](../../extensibility/internals/source-control.md)

 討論用來實作原始檔控制的整合功能，為選項[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。

---
title: 提供的服務 (原始檔控制 VSPackage) |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- services, source control packages
- source control packages, services
ms.assetid: 9db07d70-87d2-4401-bc88-e3a49d81e9a2
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4f9a4a873f2b6b3f41bd86d046bc187c17f063f1
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56601149"
---
# <a name="services-provided-source-control-vspackage"></a>提供的服務 (原始檔控制 VSPackage)
服務是透過此功能會共用 Vspackage 之間，以及 Visual Studio 整合式的開發環境 (IDE) 和其已安裝的 Vspackage 之間的主要機制。 如需詳細的服務和其重要性，Visual Studio IDE 中的詳細說明，請參閱[使用和提供服務](../../extensibility/using-and-providing-services.md)。

## <a name="the-source-control-service"></a>原始檔控制服務
 Visual Studio 提供兩個服務、 IDE 層級的服務和封裝層級的服務層。 Visual Studio IDE 本身會提供 IDE 層級的服務。 原始檔控制套件會取用這些服務。 為 VSPackage 的原始檔控制套件共用其原始檔控制功能藉由提供自己的私用的原始檔控制服務。 原始檔控制套件封裝控制相關由它的形式，可供 Visual Studio IDE 的合約實作之介面的來源的集合。

## <a name="see-also"></a>另請參閱
- [設計元素](../../extensibility/internals/source-control-vspackage-design-elements.md)
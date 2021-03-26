---
title: 提供 (原始檔控制 VSPackage 的服務) |Microsoft Docs
description: 瞭解 Vspackage 如何透過服務共用功能，包括與 Visual Studio IDE 和其 Vspackage 互動。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- services, source control packages
- source control packages, services
ms.assetid: 9db07d70-87d2-4401-bc88-e3a49d81e9a2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: fe1d9ee9805e6e86595f3f7f3cf640114c7030b9
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105080810"
---
# <a name="services-provided-source-control-vspackage"></a>提供的服務 (原始檔控制 VSPackage)
服務是主要的機制，可讓您在 Vspackage 和 Visual Studio 整合式開發環境之間共用功能 (IDE) 及其安裝的 Vspackage。 如需服務及其在 Visual Studio IDE 中重要性的詳細說明，請參閱[使用和提供服務](../../extensibility/using-and-providing-services.md)。

## <a name="the-source-control-service"></a>原始檔控制服務
 Visual Studio 提供兩個層級的服務，也就是 IDE 層級的服務和封裝層級的服務。 Visual Studio IDE 原本就提供 IDE 層級的服務。 原始檔控制封裝會使用其中一些服務。 VSPackage 的原始檔控制封裝會提供自己的私用原始檔控制服務，以共用其原始檔控制功能。 原始檔控制封裝會以可供 Visual Studio IDE 使用之合約的形式，封裝一組由原始檔控制相關聯的介面。

## <a name="see-also"></a>另請參閱
- [設計元素](../../extensibility/internals/source-control-vspackage-design-elements.md)

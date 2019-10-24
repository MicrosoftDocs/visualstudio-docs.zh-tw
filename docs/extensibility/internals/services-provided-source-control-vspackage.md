---
title: 提供的服務（原始檔控制 VSPackage） |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- services, source control packages
- source control packages, services
ms.assetid: 9db07d70-87d2-4401-bc88-e3a49d81e9a2
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 13be907eeb35a2d4382fb63726c09cb2924e57e7
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72723863"
---
# <a name="services-provided-source-control-vspackage"></a>提供的服務 (原始檔控制 VSPackage)
服務是主要的機制，可讓您在 Vspackage 之間，以及 Visual Studio 整合式開發環境（IDE）與其安裝的 Vspackage 之間共用功能。 如需服務的詳細描述及其在 Visual Studio IDE 中的重要性，請參閱[使用和提供服務](../../extensibility/using-and-providing-services.md)。

## <a name="the-source-control-service"></a>原始檔控制服務
 Visual Studio 提供兩層服務： IDE 層級服務和封裝層級服務。 Visual Studio IDE 原本就提供 IDE 層級的服務。 原始檔控制封裝會耗用其中一些服務。 作為 VSPackage 的原始檔控制套件會藉由提供自己的私用原始檔控制服務來共用其原始檔控制功能。 原始檔控制封裝會以可由 Visual Studio IDE 使用的合約形式，來封裝其所實作為原始檔控制相關介面的集合。

## <a name="see-also"></a>請參閱
- [設計元素](../../extensibility/internals/source-control-vspackage-design-elements.md)
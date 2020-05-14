---
title: 提供的服務(來源控制 VS 套件) |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- services, source control packages
- source control packages, services
ms.assetid: 9db07d70-87d2-4401-bc88-e3a49d81e9a2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f08ebe49756b442ef474ac2a032a72894f6bec15
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705400"
---
# <a name="services-provided-source-control-vspackage"></a>提供的服務 (原始檔控制 VSPackage)
服務是 VS 包之間以及 Visual Studio 整合式開發環境 (IDE) 及其已安裝的 VS 包之間共用功能的主要機制。 有關服務及其在可視化工作室 IDE 中的重要性的詳細說明,請參閱[使用和提供服務](../../extensibility/using-and-providing-services.md)。

## <a name="the-source-control-service"></a>原始碼管理服務
 Visual Studio 提供兩層服務,IDE 級服務和包級服務。 視覺工作室 IDE 本機提供 IDE 級服務。 原始程式碼管理包會消耗其中一些服務。 作為 VSPackage 的原始程式碼管理包透過提供自己的私有原始碼管理服務來共用其原始程式碼管理功能。 原始程式碼管理包封裝了它以可用於 Visual Studio IDE 的協定形式實現的原始程式碼管理相關介面集。

## <a name="see-also"></a>另請參閱
- [設計元素](../../extensibility/internals/source-control-vspackage-design-elements.md)

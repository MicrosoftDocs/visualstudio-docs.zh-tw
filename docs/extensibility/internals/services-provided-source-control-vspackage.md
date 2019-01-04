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
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5cbc107b1b300538cf9a94a89a77d8ac9e2ff728
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53828533"
---
# <a name="services-provided-source-control-vspackage"></a>提供的服務 (原始檔控制 VSPackage)
服務是透過此功能會共用 Vspackage 之間，以及 Visual Studio 整合式的開發環境 (IDE) 和其已安裝的 Vspackage 之間的主要機制。 如需詳細的服務和其重要性，Visual Studio IDE 中的詳細說明，請參閱[使用和提供服務](../../extensibility/using-and-providing-services.md)。  
  
## <a name="the-source-control-service"></a>原始檔控制服務  
 Visual Studio 提供兩個服務、 IDE 層級的服務和封裝層級的服務層。 Visual Studio IDE 本身會提供 IDE 層級的服務。 原始檔控制套件會取用這些服務。 為 VSPackage 的原始檔控制套件共用其原始檔控制功能藉由提供自己的私用的原始檔控制服務。 原始檔控制套件封裝控制相關由它的形式，可供 Visual Studio IDE 的合約實作之介面的來源的集合。  
  
## <a name="see-also"></a>另請參閱  
 [設計元素](../../extensibility/internals/source-control-vspackage-design-elements.md)
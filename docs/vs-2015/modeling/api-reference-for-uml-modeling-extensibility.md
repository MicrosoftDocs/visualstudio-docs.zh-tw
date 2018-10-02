---
title: UML 模型擴充性 API 參考 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML - extending
- UML API
- UML model, API
ms.assetid: 2b2ffe93-c358-4d28-a5e5-3d0474629b58
caps.latest.revision: 11
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: db042d59ce5f7363d9ed45e2baebbea45d3a0de4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47491601"
---
# <a name="api-reference-for-uml-modeling-extensibility"></a>UML 模型擴充性的 API 參考
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[UML 模型擴充性的 API 參考](https://docs.microsoft.com/visualstudio/modeling/api-reference-for-uml-modeling-extensibility)。  
  
您可以撰寫程式碼來讀取和修改使用 Visual Studio 建立的模型。 應用程式開發介面參考提供特定類別的相關資訊，協助您完成這項作業。 以工作為導向的詳細資訊，請參閱底下的主題[擴充 UML 模型和圖表](../modeling/extend-uml-models-and-diagrams.md)。 若要查看哪些版本的 Visual Studio 支援 UML 模型，請參閱[architecture and modeling tools 的版本支援](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)。  
  
## <a name="assemblies"></a>組件  
  
|組件|這可讓您執行|  
|--------------|--------------------------------|  
|Microsoft.VisualStudio.Uml.Interfaces.dll|-讀取和變更模型項目，例如 IUseCase、 IAssociation 等等。<br />瀏覽項目之間的關聯性。<br /><br /> 與 UML 規格所定義者相對應的命名空間和類型。|  
|Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll|-建立新的執行個體的模型項目<br />-存取和修改圖形和圖表。|  
  
## <a name="see-also"></a>另請參閱  
 [擴充 UML 模型和圖表](../modeling/extend-uml-models-and-diagrams.md)   
 [Modeling SDK for Visual Studio 的 API 參考](../modeling/api-reference-for-modeling-sdk-for-visual-studio.md)




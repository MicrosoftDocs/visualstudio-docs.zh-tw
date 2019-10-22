---
title: UML 模型擴充性的 API 參考 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
helpviewer_keywords:
- UML - extending
- UML API
- UML model, API
ms.assetid: 2b2ffe93-c358-4d28-a5e5-3d0474629b58
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e48bf723b8b1cb77cc1f7f4de9cfb562caccde84
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672800"
---
# <a name="api-reference-for-uml-modeling-extensibility"></a>UML 模型擴充性的 API 參考
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以撰寫程式碼來讀取和修改使用 Visual Studio 建立的模型。 應用程式開發介面參考提供特定類別的相關資訊，協助您完成這項作業。 如需更多工導向資訊，請參閱[擴充 UML 模型和圖表](../modeling/extend-uml-models-and-diagrams.md)底下的主題。 若要查看哪些 Visual Studio 版本支援 UML 模型，請參閱 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)。

## <a name="assemblies"></a>組件

|Assembly|這可讓您執行|
|--------------|--------------------------------|
|Microsoft.VisualStudio.Uml.Interfaces.dll|-讀取和變更模型元素，例如 IUseCase、IAssociation 等等。<br />-導覽元素之間的關聯性。<br /><br /> 與 UML 規格所定義者相對應的命名空間和類型。|
|Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll|-建立模型元素的新實例<br />-存取和修改圖形和圖表。|

## <a name="see-also"></a>請參閱
 [擴充 UML 模型和圖表](../modeling/extend-uml-models-and-diagrams.md) [API 參考，以用於 VISUAL STUDIO 的模型 SDK](../modeling/api-reference-for-modeling-sdk-for-visual-studio.md)

---
title: 視覺效果和模型 SDK 支援的 Visual Studio 版本 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, supported Visual Studio editions
ms.assetid: 7c313ba0-031d-45b8-8220-eead61754747
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0692efefcc92e3316ccf725c586fc6566b09a6ef
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2020
ms.locfileid: "75850771"
---
# <a name="supported-visual-studio-editions-for-visualization-amp-modeling-sdk"></a>視覺效果 &amp; 模型 SDK 支援的 Visual Studio 版本
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

以下是在撰寫和部署環境中 [!INCLUDE[dsl](../includes/dsl-md.md)] 支援的 Visual Studio 版本清單。 如需這些版本的詳細資訊，請參閱 Microsoft [!INCLUDE[vsprvs](../includes/vsprvs-md.md)][開發人員中心](https://msdn.microsoft.com/vstudio/products/)。

## <a name="authoring-edition"></a>撰寫版本
 若要定義 DSL，您必須已安裝下列元件：

|||
|-|-|
|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]|[http://go.microsoft.com/fwlink/?LinkId=185579](https://www.visualstudio.com/)|
|Visual Studio SDK|[http://go.microsoft.com/fwlink/?LinkId=185580](https://docs.microsoft.com/azure/devops/integrate/index?view=azure-devops&viewFallbackFrom=vsts)|
|Visual Studio Visualization and Modeling SDK|[http://go.microsoft.com/fwlink/?LinkID=186128](https://docs.microsoft.com/samples/browse/?redirectedfrom=MSDN-samples)|

## <a name="deployment-editions"></a>部署版本
 [!INCLUDE[dsl](../includes/dsl-md.md)] 支援下列設定，用於部署您所建立的特定領域語言：

- Visual Studio 企業版

- Visual Studio Professional

- Visual Studio Shell （整合模式）可轉散發套件

- Visual Studio Shell (隔離模式) 可轉散發套件

> [!NOTE]
> 若要讓 DSL 能夠在 Shell 產品上執行，您必須在擴充功能資訊清單中設定**支援的 VS Edition**欄位。 如需詳細資訊，請參閱[部署特定領域語言方案](../modeling/deploying-domain-specific-language-solutions.md)。

## <a name="see-also"></a>請參閱
 [Domain-Specific Language Tools Glossary](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa) (特定領域語言工具字彙表)

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
ms.openlocfilehash: 3eebefeab6b78955b03d4546a60dd811f5e9ae4e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547650"
---
# <a name="supported-visual-studio-editions-for-visualization-amp-modeling-sdk"></a>視覺效果模型 SDK 支援的 Visual Studio 版本 &amp;
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

以下是 [!INCLUDE[dsl](../includes/dsl-md.md)] 在撰寫和部署環境中支援之 Visual Studio 版本的清單。 如需這些版本的詳細資訊，請參閱 Microsoft [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] [開發人員中心](https://msdn.microsoft.com/vstudio/products/)。

## <a name="authoring-edition"></a>撰寫版本
 若要定義 DSL，您必須已安裝下列元件：

|產品|下載連結|
|-|-|
|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]|[https://www.visualstudio.com/](https://www.visualstudio.com/)|
|[!INCLUDE[vssdk_current_short](../includes/vssdk-current-short-md.md)]|[Visual Studio SDK](../extensibility/visual-studio-sdk.md)|
|Visual Studio Visualization and Modeling SDK|[模型 SDK 下載](https://www.microsoft.com/download/details.aspx?id=48148)|
## <a name="deployment-editions"></a>部署版本
 [!INCLUDE[dsl](../includes/dsl-md.md)] 支援下列設定來部署您所建立的網域特定語言：

- Visual Studio Enterprise

- Visual Studio Professional

- Visual Studio Shell (整合模式) 可轉散發套件

- Visual Studio Shell (隔離模式) 可轉散發套件

> [!NOTE]
> 若要讓 DSL 能夠在 Shell 產品上執行，您必須在延伸模組資訊清單中設定 **支援的 VS Edition** 欄位。 如需詳細資訊，請參閱[部署特定領域語言方案](../modeling/deploying-domain-specific-language-solutions.md)。

## <a name="see-also"></a>另請參閱
 [Domain-Specific Language Tools Glossary](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa) (特定領域語言工具字彙表)

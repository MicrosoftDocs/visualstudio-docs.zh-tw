---
title: 視覺效果和模型 SDK 支援的 Visual Studio 版本
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, supported Visual Studio editions
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 127b45ae6a0ab28d7f83ee41449d7846858ee4a9
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591901"
---
# <a name="supported-visual-studio-editions-for-visualization--modeling-sdk"></a>支援的 Visual Studio Visualization & Modeling SDK 版本

以下是在撰寫和部署環境中 [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] 支援的 Visual Studio 版本清單。 如需這些版本的詳細資訊，請參閱 Microsoft Visual Studio[開發人員中心](https://visualstudio.microsoft.com/)。

## <a name="authoring-edition"></a>撰寫版本

若要定義 DSL，您必須已安裝下列元件：

|||
|-|-|
|Visual Studio|[http://go.microsoft.com/fwlink/?LinkId=185579](https://visualstudio.microsoft.com/)|
|Visual Studio SDK|[http://go.microsoft.com/fwlink/?LinkId=185580](/azure/devops/integrate/index?view=azure-devops&viewFallbackFrom=vsts)|
|Visual Studio Visualization and Modeling SDK|[http://go.microsoft.com/fwlink/?LinkID=186128](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db)|

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="deployment-editions"></a>部署版本

[!INCLUDE[dsl](../modeling/includes/dsl_md.md)] 支援下列設定，用於部署您所建立的特定領域語言：

- Visual Studio 企業版

- Visual Studio Professional

- Visual Studio Shell （整合模式）可轉散發套件

- Visual Studio Shell (隔離模式) 可轉散發套件

> [!NOTE]
> 若要讓 DSL 能夠在 Shell 產品上執行，您必須在擴充功能資訊清單中設定**支援的 VS Edition**欄位。 如需詳細資訊，請參閱[部署特定領域語言方案](msi-and-vsix-deployment-of-a-dsl.md)。

## <a name="see-also"></a>請參閱

- [Domain-Specific Language Tools Glossary](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa) (特定領域語言工具字彙表)

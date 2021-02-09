---
title: 視覺效果和模型 SDK 支援的 Visual Studio 版本
description: 瞭解在撰寫和部署環境中支援 DSL 工具的 Visual Studio 版本。
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, supported Visual Studio editions
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 14c23df472361fdee0bc657eb277d3a6bef4be73
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99899695"
---
# <a name="supported-visual-studio-editions-for-visualization--modeling-sdk"></a>支援的 Visual Studio Visualization & Modeling SDK 版本

以下是 [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] 在撰寫和部署環境中支援之 Visual Studio 版本的清單。 如需這些版本的詳細資訊，請參閱 Microsoft Visual Studio [開發人員中心](https://visualstudio.microsoft.com/)。

## <a name="authoring-edition"></a>撰寫版本

若要定義 DSL，您必須已安裝下列元件：

|產品|下載連結|
|-|-|
|Visual Studio|[http://go.microsoft.com/fwlink/?LinkId=185579](https://visualstudio.microsoft.com/)|
|Visual Studio SDK|[http://go.microsoft.com/fwlink/?LinkId=185580](/azure/devops/integrate/index?view=azure-devops&viewFallbackFrom=vsts&preserve-view=true)|
|Visual Studio Visualization and Modeling SDK|[http://go.microsoft.com/fwlink/?LinkID=186128](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db)|

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="deployment-editions"></a>部署版本

[!INCLUDE[dsl](../modeling/includes/dsl_md.md)] 支援下列設定來部署您所建立的網域特定語言：

- Visual Studio Enterprise

- Visual Studio Professional

- Visual Studio Shell (整合模式) 可轉散發套件

- Visual Studio Shell (隔離模式) 可轉散發套件

> [!NOTE]
> 若要讓 DSL 能夠在 Shell 產品上執行，您必須在延伸模組資訊清單中設定 **支援的 VS Edition** 欄位。 如需詳細資訊，請參閱[部署特定領域語言方案](msi-and-vsix-deployment-of-a-dsl.md)。

## <a name="see-also"></a>另請參閱

- [Domain-Specific Language Tools Glossary](/previous-versions/bb126564(v=vs.100)) (特定領域語言工具字彙表)
---
title: 使用設定檔和造型自訂您的模型 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML model, profiles
- UML model, stereotypes
- UML model, customizing
ms.assetid: fd607157-0d3a-4583-a84e-427a4b2a5acb
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4f83fcf3ea500e0640a226b80d3d3c0e2c7ed869
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655095"
---
# <a name="customize-your-model-with-profiles-and-stereotypes"></a>使用設定檔和造型自訂您的模型
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在 Visual Studio 中，您可以採用標準 UML 模型項目，例如類別和元件，針對特定用途自訂它們。 您可以將造型*套用至模型專案，以*變更元素的屬性清單。 造型是在稱為*設定檔*的集合中定義。

 若要查看哪些 Visual Studio 版本支援這項功能，請參閱 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)。

 若要使用造型，請將套件連結至設定檔。 這可讓您將設定檔中定義的造型套用至套件中的項目。 某些設定檔會與 Visual Studio 一起安裝。 此外，您可以定義自己的設定檔。

 在項目的屬性清單中，可以設定造型。 針對圖表上的主要圖形類型，已套用的造型也會出現在圖形中，如範例中所示。

 ![具有造型的 UML 類別。](../modeling/media/uml-class-stereotype.png "UML_class_stereotype")

> [!NOTE]
> 如果您使用設定檔來建立模型，然後與其他人共用模型，他們將無法看到造型，除非他們的電腦上安裝了相同的設定檔。

## <a name="related-topics"></a>相關主題

|標題|描述|
|-----------|-----------------|
|[將造型新增至 UML 模型項目](../modeling/add-stereotypes-to-uml-model-elements.md)|將模型項目放在套件中、將套件連結至設定檔，然後將造型套用至項目。|
|[UML 模型的標準造型](../modeling/standard-stereotypes-for-uml-models.md)|UML 標準設定檔 L2 和 L3 隨 Visual Studio 一起安裝，且依預設每個模型會連結到它們。 它們提供您可以用來為模型加上註解的造型。<br /><br /> 例如，您可以套用 «規格» 造型到類別，表示它只是要定義其執行個體的外在可見行為。|
|[定義要擴充 UML 的設定檔](../modeling/define-a-profile-to-extend-uml.md)|您可以定義自己的造型和工具，以適應您自己的應用程式區域。<br /><br /> 例如，如果您開發銀行業務軟體，您可以定義 «帳戶» 造型，以便將它套用到類別。 您接著可以使用類別圖來描述不同類型的帳戶和其關聯性。|
|[安裝 UML 設定檔](../modeling/install-a-uml-profile.md)|如果有人給您 UML 設定檔，您可以在電腦上安裝它。|
|[定義自訂模型工具箱項目](../modeling/define-a-custom-modeling-toolbox-item.md)|自訂工具箱項目能讓您不必反覆地在新的項目上設定造型。|
|[依造型著色 UML 類別](http://code.msdn.microsoft.com/UML-Color-Classes-by-07de2b70)|此範例程式碼會擴充 UML 圖表。 它會自動根據項目的造型設定 UML 圖形的色彩。|

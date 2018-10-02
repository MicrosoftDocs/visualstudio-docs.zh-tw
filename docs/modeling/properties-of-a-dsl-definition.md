---
title: DSL 定義的屬性
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, definition file
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: a2f919e1dce6864fa25348acd9c9858f9e4022f8
ms.sourcegitcommit: ad5fb20f18b23eb8bd2568717f61edc6b7eee5e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47857699"
---
# <a name="properties-of-a-dsl-definition"></a>DSL 定義的屬性
DslDefinition 屬性會定義*定義域專屬語言*定義屬性，例如版本編號。 DslDefinition 屬性會出現在**屬性**視窗中，當您按一下圖中的開放區域*特定領域語言設計工具*。

 如需詳細資訊，請參閱 <<c0> [ 如何定義特定領域語言](../modeling/how-to-define-a-domain-specific-language.md)。 如需如何使用這些屬性的詳細資訊，請參閱[自訂及擴充特定領域語言](../modeling/customizing-and-extending-a-domain-specific-language.md)。

 DslDefinition 具有下表中的屬性：

|屬性|描述|預設|
|--------------|-----------------|-------------|
|存取修飾詞|判斷領域類別的存取修飾詞為公用或內部。|public|
|自訂屬性|自訂定義網域類別的屬性。<br /><br /> **請注意**使用瀏覽按鈕以新增屬性。|\<無 >|
|公司名稱|目前的公司名稱，在系統登錄的名稱。|目前的公司名稱|
|名稱|這個領域類別的名稱。|目前的名稱|
|命名空間|與此領域類別相關的命名空間。|目前的命名空間|
|套件 Guid|為此 dsl 產生之 Visual Studio 套件 guid。|\<無 >|
|封裝命名空間|為此 dsl 產生之 Visual Studio 套件命名空間。|\<無 >|
|產品名稱|將註冊為此 dsl 產生之 Visual Studio 套件的產品名稱。|\<無 >|
|注意|與此領域類別相關聯的資訊。|\<無 >|
|描述|此網域類別的描述。|\<無 >|
|顯示名稱|將會顯示在這個網域類別產生的設計工具的名稱。|\<無 >|
|說明關鍵字|與此領域類別相關聯的 help 關鍵字。|\<無 >|
|組建|如需此特定領域語言定義累加的組建編號。|0|
|主要版本|此特定領域語言定義增量的主要組建編號。|1|
|次要版本|如需此特定領域語言定義增量的次要組建數目。|0|
|修訂|累加修訂建置這個特定領域語言定義的數字。|0|

## <a name="see-also"></a>另請參閱

- [特定領域語言工具字彙](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
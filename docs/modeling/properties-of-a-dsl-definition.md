---
title: DSL 定義的屬性
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, definition file
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ee23e15e6cc389ea5a8bdcdd793648365d08c30d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85532298"
---
# <a name="properties-of-a-dsl-definition"></a>DSL 定義的屬性
Dsldefinition.dsl 檔屬性會定義 *網域特定語言* 定義屬性，例如版本編號。 當您在*特定領域語言設計工具*中按一下圖表的開啟區域時，dsldefinition.dsl 檔屬性就會出現在 [**屬性**] 視窗中。

 如需詳細資訊，請參閱 [如何定義網域指定的語言](../modeling/how-to-define-a-domain-specific-language.md)。 如需有關如何使用這些屬性的詳細資訊，請參閱 [自訂和擴充特定領域語言](../modeling/customizing-and-extending-a-domain-specific-language.md)。

 Dsldefinition.dsl 檔具有下表中的屬性：

|屬性|描述|預設|
|-|-|-|
|存取修飾詞|判斷網域類別的存取修飾詞為公用或內部。|public|
|自訂屬性|網域類別的自訂已定義屬性。<br /><br /> **注意** 使用 [流覽] 按鈕來新增屬性。|\<none>|
|公司名稱|系統登錄中目前公司名稱的名稱。|目前的公司名稱|
|Name|這個網域類別的名稱。|目前的名稱|
|命名空間|與這個網域類別關聯的命名空間。|目前的命名空間|
|套件 Guid|為此 DSL 產生之 Visual Studio 套件的 guid。|\<none>|
|封裝命名空間|為此 DSL 產生之 Visual Studio 套件的命名空間。|\<none>|
|產品名稱|將為此 DSL 產生之 Visual Studio 套件註冊的產品名稱。|\<none>|
|附註|與此網域類別相關的附注。|\<none>|
|描述|此網域類別的描述。|\<none>|
|顯示名稱|將在為這個網域類別產生的設計工具中顯示的名稱。|\<none>|
|說明關鍵字|與這個網域類別相關聯的 help 關鍵字。|\<none>|
|Build|這個網域特定語言定義的累加組建編號。|0|
|主要版本|這個網域特定語言定義的累加主要組建編號。|1|
|次要版本|這個網域特定語言定義的累加次要組建編號。|0|
|修訂版|這個網域特定語言定義的累加式修訂組建編號。|0|

## <a name="see-also"></a>另請參閱

- [Domain-Specific Language Tools Glossary](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa) (特定領域語言工具字彙表)
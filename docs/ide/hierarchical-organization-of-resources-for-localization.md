---
title: 階層式組織當地語系化的資源
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- resource files, localized
- localization [Visual Studio], resources
- fallback resources
- international applications [Visual Studio], storing resources
- satellite assemblies, resource hierarchies
- globalization [Visual Studio], resources
- satellite assemblies
- resources [Visual Studio], fallback system
- resource files, fallback processes
ms.assetid: dadf8f2c-f74c-44d7-bec0-a1e956d8d38d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4df50f1336f235d50d7c897deb2450469f9128b8
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55038600"
---
# <a name="hierarchical-organization-of-resources-for-localization"></a>階層式組織當地語系化的資源

在 Visual Studio 中，當地語系化資源 (例如適用於各文化的字串和影像資料) 會儲存在不同的檔案中，並根據 UI 文化特性設定載入。 若要了解當地語系化資源載入的方式，最好將它們視為以階層方式組織而成。

## <a name="kinds-of-resources-in-the-hierarchy"></a>階層中的資源類型

- 階層頂端是您預設文化特性 (Culture) 的後援資源，例如英文 ("en")。 這些後援資源是唯一不具有本身專屬檔案的資源；它們會儲存於主要組件中。

- 在後援資源之下是任何中性文化特性的資源。 中性文化特性與語言相關聯，而不是與國家/地區關聯。 例如，法文 ("fr") 是中性文化特性。 (後援資源同樣也是中性文化特性 (Culture)，但它是特殊的)。

- 在中性文化特性 (Culture) 資源之下是任何特定文化特性 (Culture) 的資源。 特定文化特性與語言及國家/地區相關聯。 例如，加拿大法文 ("fr-CA") 是特定文化特性。

如果應用程式嘗試載入任一當地語系化資源 (例如字串)，但找不到資源，則它會在階層架構中尋找，直到找到包含所要求資源的資源檔。

儲存您資源的最佳方式是盡可能地將它們一般化。 也就是盡可能將當地語系化字串、影像等等儲存在中性文化特性的資源檔中，而不是特定文化特性。 舉例來說，如果您有適用於比利時法文 ("fr-BE") 文化特性的資源，而在該資源之上即為使用英文的後援資源，則當某些人在設定為加拿大法文文化特性的系統上使用您的應用程式時，可能會造成問題。 系統會尋找 "fr-CA" 的附屬組件，但找不到，因此會載入包含後援資源的主要組件 (英文)，而不是載入法文資源。 下圖顯示此不適當的案例。

![只限特定資源](../ide/media/vbspecificresourcesonly.gif)

如果您遵循建議的做法，盡可能地為 "fr" 文化特性的中性資源檔放入許多資源，則加拿大法文的使用者就不會看到標示為 "fr-BE" 文化特性的資源，但會看到字串以法文顯示。 下列情況顯示此建議的案例。

![NeutralSpecificResources 圖形](../ide/media/vbneutralspecificresources.gif)

## <a name="see-also"></a>另請參閱

- [當地語系化的中性資源語言](../ide/neutral-resources-languages-for-localization.md)
- [安全性和當地語系化附屬組件](../ide/security-and-localized-satellite-assemblies.md)
- [當地語系化應用程式](../ide/localizing-applications.md)
- [全球化和當地語系化應用程式](../ide/globalizing-and-localizing-applications.md)
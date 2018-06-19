---
title: 如何：建置到通用輸出目錄
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- output directory
- builds [Visual Studio], common directory
- common directory
ms.assetid: 1fcc2c48-07cb-4c4f-9556-36945e7dfc4e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 12f45890224684ff2e4c411875ab61bdfb698cfb
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31942041"
---
# <a name="how-to-build-to-a-common-output-directory"></a>如何：建置到通用輸出目錄

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 預設會在方案的專屬資料夾中建立方案中的每個專案。 您可以變更專案的建置輸出路徑，強制將所有輸出放在相同的資料夾中。

## <a name="to-place-all-solution-outputs-in-a-common-directory"></a>將所有方案輸出放在一個通用目錄中

1.  按一下方案中的一個專案。

2.  在 [專案] 功能表上，按一下 [屬性]。

3.  根據專案類型，按一下 [編譯] 索引標籤或 [建置] 索引標籤，然後將 [輸出路徑] 設為要用於方案中所有專案的資料夾。

4.  針對方案中的所有專案，重複步驟 1-3。

## <a name="see-also"></a>另請參閱

- [編譯及建置](../ide/compiling-and-building-in-visual-studio.md)
- [如何：變更組建輸出目錄](../ide/how-to-change-the-build-output-directory.md)
---
title: 如何：建置到通用輸出目錄
description: 瞭解如何變更專案的組建輸出路徑，以強制所有輸出放在相同的資料夾中。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: how-to
helpviewer_keywords:
- output directory
- builds [Visual Studio], common directory
- common directory
ms.assetid: 1fcc2c48-07cb-4c4f-9556-36945e7dfc4e
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2e2abb9a768621477465b753554c111126a5af98
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99967614"
---
# <a name="how-to-build-to-a-common-output-directory"></a>如何：建置到通用輸出目錄

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 預設會在方案的專屬資料夾中建立方案中的每個專案。 您可以變更專案的建置輸出路徑，強制將所有輸出放在相同的資料夾中。

## <a name="to-place-all-solution-outputs-in-a-common-directory"></a>將所有方案輸出放在一個通用目錄中

1. 按一下方案中的一個專案。

2. 按一下 [專案]  功能表上的 [屬性]  。

3. 根據專案類型，按一下 [編譯] 索引標籤或 [建置] 索引標籤，然後將 [輸出路徑] 設為要用於方案中所有專案的資料夾。

4. 針對方案中的所有專案，重複步驟 1-3。

## <a name="see-also"></a>另請參閱

- [編譯和建置](../ide/compiling-and-building-in-visual-studio.md)
- [如何：變更組建輸出目錄](../ide/how-to-change-the-build-output-directory.md)
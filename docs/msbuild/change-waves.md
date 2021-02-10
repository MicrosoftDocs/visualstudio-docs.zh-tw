---
title: 變更波浪
description: 瞭解如何啟用或停用 MSBuild 中可能有干擾的功能。
ms.date: 11/10/2020
ms.topic: conceptual
helpviewer_keywords:
- Change waves [MSBuild]
- MSBuildDisableFeaturesFromVersion environment variable
author: ghogen
ms.author: ghogen
manager: jmartens
monikerRange: '>=vs-2019'
ms.workload:
- multiple
ms.openlocfilehash: 77f93b4741ee987bac871e619ccbe58e2d4d4000
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99939522"
---
# <a name="change-waves"></a>變更波浪

*變更 wave* 是 MSBuild 中的一組行為變更，您可以藉由指定特定旗標作為環境變數來退出。 其目的是要警告您可能發生的干擾性變更，讓您可以彈性地在這些變更成為標準功能之前，對這些變更進行調整。 特定變更波中的所有功能只能一起啟用或停用，而不是個別啟用或停用。

當您升級至新版本的 MSBuild 時，預設會啟用可能中斷的變更，但如果功能對您的組建有負面影響，您就可以輕鬆地停用該變更。 每個變更波都是以 MSBuild 版本號碼來識別 (例如 16.8) ，但設定變更 wave 只會控制可能影響組建程式的某些功能，而不是該 MSBuild 版本中的所有變更。 [本文稍後](#change-waves-and-associated-features)會顯示每個變更波的功能清單。 停用變更 wave 也會停用較高版本的變更波。

## <a name="opt-out-of-change-wave-features"></a>退出變更 wave 功能

若要停用變更 wave 中的功能，請將環境變數設定 `MSBuildDisableFeaturesFromVersion` 為變更 wave (或包含您想要 **停用** 之功能的 MSBuild 版本) 。 這是開發功能的 MSBuild 版本。 請參閱以下各項功能的變更波浪對應。

### <a name="msbuilddisablefeaturesfromversion-values"></a>MSBuildDisableFeaturesFromVersion 值

如果您未設定為有效的變更波，您將會收到特定 wave 的警告和/或預設值 `MSBuildDisableFeaturesFromVersion` 。 下表顯示可能的設定：

| `MSBuildDisableFeaturesFromVersion` 值                         | 結果        | 收到警告嗎？ |
| :-------------                                                    | :----------   | :----------: |
| 本組                                                             | 啟用所有的變更，這表示每個變更波背後的所有功能都會啟用。               | 否   |
| 任何有效和目前的變更波 (例如 `16.8`)                       | 停用變更 wave 和更新 `16.8` **版本** 背後的所有功能。                                           | 否   |
| 不正確值 (例如， `16.9` 當有效的波浪為 `16.8` 和 `16.10`) | 預設值為最接近的有效值 (遞增) 。 例如，設定 `16.9` 會將您預設為 `16.10` 。               | 否   |
| 不旋轉 (例如， `17.1` 當最高波 `17.0`) 時      | 將其設為最接近的有效值。 例如， `17.1` 個至 `17.0` ，並 `16.5` 個至 `16.8`                    | 是  |
| 不正確格式 (例如， `16x8` 、 `17_0` 、 `garbage`)                     | 啟用所有的變更，這表示每個變更波背後的所有功能都會啟用。               | 是  |

## <a name="change-waves-and-associated-features"></a>變更波浪和相關聯的功能

下列清單中的連結會移至該功能的 GitHub PR。

### <a name="168"></a>16.8

- [啟用 NoWarn](https://github.com/dotnet/msbuild/pull/5671)
- [將目標/工作略過的記錄訊息截斷為1024個字元](https://github.com/dotnet/msbuild/pull/5553)
- [請勿使用 false 條件展開完整磁片磁碟機 glob](https://github.com/dotnet/msbuild/pull/5669)

### <a name="1610"></a>16.10

- [條件中的屬性展開有空白字元時發生錯誤](https://github.com/dotnet/msbuild/pull/5672)

### <a name="170"></a>17.0

此變更 wave 中沒有任何專案。

## <a name="change-waves-that-are-out-of-rotation"></a>變更不是旋轉的波浪

目前沒有任何輪替變更。

## <a name="faq"></a>常見問題集

**為什麼要以其他每個版本為目標來輪替變更？**

我們相信這是足夠的時間來與受影響的人員討論，並協助調整變更。

**為何要使用環境變數而不是專案屬性？**

在某些情況下，我們想要在 MSBuild 載入專案之前，先在變更波下放置一項功能。 基於這個理由，變更波需要使用環境變數。

**退出宣告的原因為何？**

退出宣告是比較好的方法，否則當某個功能影響客戶組建時，可能會獲得有限的意見反應。

## <a name="see-also"></a>另請參閱

- [MSBuild](msbuild.md)
- [MSBuild 16 的新功能](whats-new-msbuild-16-0.md)

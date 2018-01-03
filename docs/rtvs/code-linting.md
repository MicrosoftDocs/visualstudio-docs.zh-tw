---
title: "使用 Visual Studio R 工具進行 Linting | Microsoft Docs"
ms.custom: 
ms.date: 12/04/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-r
ms.devlang: r
ms.tgt_pltfrm: 
f1_keywords: vs.toolsoptionspages.text_editor.r.lint
ms.topic: article
caps.latest.revision: "1"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload: data-science
ms.openlocfilehash: 76f4ceb040e62e4ebac46e8a791f5dac0d73aff5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="linting-r-code-in-visual-studio"></a>在 Visual Studio 中對 R 程式碼進行 Linting

Linting 是一種分析程式碼以揭露潛在錯誤、格式問題，以及程式碼檔案中其他雜訊 (例如假性空白) 的過程。 Linting 也有助於鼓勵特定程式碼撰寫慣例，例如如何命名識別碼。這在小組和其他共同作業的情況下很有幫助。

Visual Studio R 工具 (RTVS) 可為 R 提供內建的 Linting，其行為可透過各種選項控制。 這些選項可在 [工具] > [選項] > [文字編輯器] > [R] > [Lint] 中找到。

根據預設，Linting 為停用。 若要啟用 Linting，請將 [所有設定] > [Enable lint] (啟用 Lint) 選項設為 [True]。 跟隨此主題的其他章節會描述所有其他 Linting 選項：

當啟用時，Linting 會在您於編輯器中鍵入時套用。 問題會以綠色波浪線的形式顯示。 例如，在下圖中，RTVS 發現了六個 Linting 問題，包括使用 `=` 進行指派而非 `<-`、在函式引數周圍缺少間距、使用 Pascal 命名法及大寫識別碼，以及使用分號。 將滑鼠游標在問題上暫留會顯示問題的描述。

![R 程式碼 Linting 的範例](media/linting-01.png)

## <a name="assignment-group"></a>指派群組

| 選項 | 預設值 | Linting 效果 |
| --- | --- | --- |
| 強制使用 \<- | `True` | 當並未使用 `<-` 進行指派時識別問題。 |

## <a name="naming-group"></a>命名群組

這些選項會為使用不同命名慣例的識別碼加上旗標：

| 選項 | 預設值 | Linting 效果 |
| --- | --- | --- |
| 為 camelCase 加上旗標 | `False` | 為使用 camelCase 的識別碼加上旗標。 |
| 為長名稱加上旗標 | `False` | 為名稱超過「名稱長度上限」設定的識別碼加上旗標。 |
| 為多個點 (.) 加上旗標 | `True` | 為使用多個點的識別碼加上旗標。 |
| 為 PascalCase 加上旗標 | `True` | 為使用 PascalCase 的識別碼加上旗標。 |
| 為 snake_case 加上旗標 | `False` | 為使用 snake_case 的識別碼加上旗標。 |
| 為大寫加上旗標 | `True` | 為全部使用大寫字母命名的識別碼加上旗標。 |
| 名稱長度上限 | 32 | 使用「為長名稱加上旗標」設定時套用的長度設定。 |

## <a name="spacing-group"></a>間距群組

根據預設，這些選項全部都已設為 `True`，其會控制 Linter 如何識別間距問題：函式名稱之後、逗號周圍、運算子周圍、左雙引號及右雙引號位置、( 之前的空白，以及 () 內部的空白。

## <a name="statements-group"></a>陳述式群組

| 選項 | 預設值 | Linting 效果 |
| --- | --- | --- |
| 選擇性顯示 | `True` | 當多個陳述式位於同一行時識別問題。 |
| 分號 | `True` | 識別分號的使用。 |

## <a name="text-group"></a>文字群組

| 選項 | 預設值 | Linting 效果 |
| --- | --- | --- |
| 行長度限制 | `False` | 設定 Linter 是否要為超過「行長度上限」選項的行加上旗標。 |
| 行長度上限 | 80 | 使用「行長度限制」選項時套用的長度限制。 |

## <a name="whitespace-group"></a>空白字元群組

根據預設，這些選項全部都已設為 `True`，其會控制 Linter 如何識別空白字元問題：Tab 鍵的使用、雙引號的使用、後置空白行，以及後置空白字元。
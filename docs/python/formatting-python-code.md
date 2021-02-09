---
title: 格式化 Python 程式碼
description: Visual Studio 可以自動重新設定 Python 程式碼格式，包括間距、陳述式、換行和註解。
ms.date: 03/13/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 7b03e99a70edd587c9dfe2a43d326a64d14b9193
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99887883"
---
# <a name="format-python-code"></a>格式化 Python 程式碼

Visual Studio 可讓您快速重新格式化程式碼，以符合預先設定的格式化選項。

- 若要格式化選取專案：選取 [**編輯** 高階  >    >  **格式選取專案**] 或按 **Ctrl** + **E**  >  **F**。
- 若要格式化整個檔案：選取 [**編輯**  >  **先進**  >  的 **格式** 檔] 或按 **Ctrl** + **E**  >  **D**。

選項是透過 [**工具**  >  **選項**  >  **文字編輯器**  >    >  ]、[Python **格式**] 和其嵌套索引標籤來設定。 您需要選取 [顯示所有設定] 來使這些選項出現：

![Visual Studio 中的 Python 格式選項](media/options-editor-formatting.png)

格式選項預設會設定成符合 [PEP 8 樣式指南](https://www.python.org/dev/peps/pep-0008/) \(英文\) 的超集合。 [一般] 索引標籤能決定何時套用格式；針對其他三個索引標籤的設定，會於本文章中說明。

此外，[Visual Studio 中的 Python 支援](installing-python-support-in-visual-studio.md)也會將實用的 [[填滿註解段落]](#fill-comment-paragraph-command) 命令新增至 [編輯] > [進階] 功能表中，如後續小節中所述。

## <a name="spacing"></a>間距

**間距** 控制在各種語言建構前後插入或移除空格的位置。 每個選項有三個可能的值︰

- 已核取︰確保間距已套用。
- 已清除︰移除任何間距。
- 不定︰保留原始格式。

下表提供各種選項範例：

| 類別定義選項 | 已核取 | 已清除 |
| --- | --- | --- |
| **在類別宣告的名稱與基底清單之間插入空格** | `class X (object): pass` | `class X(object): pass` |
| **在基底清單括號內插入空格** | `class X( object ): pass` | `class X(object): pass` |
| **在空白基底清單括號內插入空格** | `class X( ): pass` | `class X(): pass` |

<br/>

| 函式定義選項 | 已核取 | 已清除 |
| --- | --- | --- |
| **在函式宣告的名稱與參數清單之間插入空格** | `def X (): pass` | `def X(): pass` |
| **在參數清單括號內插入空格** | `def X( a, b ): pass` | `def X(a, b): pass` |
| **在空白的參數清單括號內插入空格** | `def X( ): pass` | `def X(): pass` |
| **在預設參數值的 '=' 前後插入空格** | `includes X(a = 42): pass` | `includes X(a=42): pass` |
| **在傳回註解運算子前後插入空格** | `includes X() -> 42: pass` | `includes X()->42: pass` |

<br/>

| 運算子選項 | 已核取 | 已清除 |
| --- | --- | --- |
| **在二元運算子前後插入空格** | `a + b` | `a+b` |
| **在指派前後插入空格** | `a = b` | `a=b` |

<br/>

| 運算式間距選項 | 已核取 | 已清除 |
| --- | --- | --- |
| **在函式呼叫的名稱與引數清單之間插入空格** | `X ()` | `X()` |
| **在空白引數清單括號內插入空格** | `X( )` | `X()` |
| **在引數清單括號內插入空格** | `X( a, b )` | `X(a, b)` |
| **在運算式的括號內插入空格** | `( a )` | `(a)` |
| **在空白元組括號內插入空格** | `( )` | `()` |
| **在元組括號內插入空格** | `( a, b )` | `(a, b)` |
| **在空白方括號中插入空格** | `[ ]` | `[]` |
| **在清單的方括號內插入空格** | `[ a, b ]` | `[a, b]` |
| **在左方括號前插入空格** | `x [i]` | `x[i]` |
| **在方括號內插入空格** | `x[ i ]` | `x[i]` |

<br/>

## <a name="statements"></a>陳述式

[陳述式] 選項控制以更多 Pythonic 格式自動重新撰寫各種陳述式。

| 選項 | 格式之前 | 格式之後 |
| --- | --- | --- |
| **將匯入的模組置於新行** | `import sys, pickle` | `import sys`<br/>`import pickle` |
| **移除不必要的分號** | `x = 42;` | `x = 42` |
| **將多個陳述式置於新行** | `x = 42; y = 100` | `x = 42`<br/>`y = 100` |

## <a name="wrapping"></a>換行

[包裝] 讓您設定 [註解寬度上限] (預設值為 80)。 如已設定 [將太寬的註解換行] 選項，Visual Studio 會重新格式化註解，使不超過寬度上限。

```python
# Wrapped to 40 columns
# There should be one-- and preferably
# only one --obvious way to do it.
```

```python
# Not-wrapped:
# There should be one-- and preferably only one --obvious way to do it.
```

## <a name="fill-comment-paragraph-command"></a>填滿註解段落命令

**編輯**  > **Advanced**  > **填滿批註段落** (**Ctrl** + **E**  >  **P**) 重排和格式化註解文字、將短行合併在一起，以及細分較長的行。

例如：

```python
# foo
# bar
# baz
```

變更為：

```python
# foo bar baz
```

```python
# This is a very long long long long long long long long long long long long long long long long long long long comment
```

變更為：

```python
# This is a very long long long long long long long long long long long long
# long long long long long long long comment
```

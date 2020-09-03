---
title: 單元測試 Python 程式碼
description: 在 Visual Studio 中設定 Python 程式碼的單元測試，以充分利用 [測試總管] 的功能來探索、執行和偵錯測試。
ms.date: 09/18/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 2a621cd56f980c8a1404ba8855cdf3544e58d39d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85535317"
---
# <a name="set-up-unit-testing-for-python-code"></a>設定 Python 程式碼的單元測試

單元測試是測試應用程式中其他程式碼單元 (通常是隔離的函數、類別等) 的程式碼片段。 應用程式通過所有單元測試之後，您至少可以確定其低階功能皆能正確運作。

在設計程式時，Python 會廣泛地使用單元測試來驗證案例。 Visual Studio 中的 Python 支援包含在開發程序的內容內針對單元測試進行探索、執行及偵錯，而且不需要個別執行測試。

本文章提供搭配 Python 的 Visual Studio 中的單元測試功能簡介。 如需單元測試的整體詳細資訊，請參閱[對程式碼進行單元測試](../test/unit-test-your-code.md)。

::: moniker range="vs-2017"

[!include[Testing Python code](includes/vs-2017/unit-testing-python.md)]

::: moniker-end

::: moniker range=">= vs-2019"

[!include[Testing Python code](includes/vs-2019/unit-testing-python.md)]

::: moniker-end
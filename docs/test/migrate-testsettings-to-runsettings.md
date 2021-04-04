---
title: 將 .testsettings 遷移至 .runsettings
description: 瞭解如何將 .testsettings 遷移至 .runsettings
ms.custom: SEO-VS-2020
ms.date: 03/18/2021
ms.topic: conceptual
f1_keywords:
- vs.UnitTest.Migrate
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ab1cfe921777fa75d4f69251668934e8d78d9bec
ms.sourcegitcommit: 155d5f0fd54ac1d20df2f5b0245365924faa3565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/31/2021
ms.locfileid: "106087181"
---
# <a name="upgrade-from--testsettings-to-runsettings"></a>從  *.testsettings* 升級至 *. .runsettings*

您可以使用隨 Visual Studio 安裝的 SettingsMigrator 工具，將測試組態檔從 *.testsettings* 升級至 *. .runsettings* 。 視您的 Visual Studio 安裝位置而定，您可以在下列路徑中找到 [設定遷移程式] 工具： `C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\Extensions\TestPlatform\SettingsMigrator.exe`

在正確的目錄位置中，您可以使用下列格式來執行此工具：

```console
SettingsMigrator.exe <Full path to testsettings file to be migrated>
SettingsMigrator.exe <Full path to testsettings file to be migrated> <Full path to runsettings file to be created>
```

## <a name="examples"></a>範例
```console
SettingsMigrator.exe E:\MyTest\MyTestSettings.testsettings
SettingsMigrator.exe E:\MyTest\MyTestSettings.testsettings E:\MyTest\MyNewRunSettings.runsettings
```

如果您想要閱讀更多有關 *.testsettings* 選項轉換的方式 *。 .runsettings* 您可以在 GitHub 上的 [開放原始碼測試平臺存放庫](https://github.com/microsoft/vstest-docs/blob/master/RFCs/0023-TestSettings-Deprecation.md#migration) 中找到更多的執行詳細資料。

## <a name="see-also"></a>另請參閱

- [使用設定測試回合 `.runsettings`](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)
- [從 MSTestv1 升級至 MSTestv2](../test/mstest-update-to-mstestv2.md)
- [對程式碼進行單元測試](../test/unit-test-your-code.md)
- [使用測試總管進行偵錯單元測試](../test/debug-unit-tests-with-test-explorer.md)

---
title: 移轉 64 位元偵錯工具 COM 類別登錄 |Microsoft Docs
ms.date: 11/10/2016
ms.topic: conceptual
ms.assetid: 45cfcee6-7a68-4d4f-b3f6-e2d8a0fa066a
author: gregg-miskelly
ms.author: greggm
manager: jillfra
ms.workload:
- greggm
ms.openlocfilehash: 74fbb959f8272be001aad8a576724d5eb1ad6157
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62433691"
---
# <a name="migrate-64-bit-debugger-com-class-registration"></a>移轉 64 位元偵錯工具 COM 類別註冊

註冊 COM 的偵錯工具擴充功能中的類別 HKEY_CLASSES_ROOT 使用 regasm，regsvr32，或直接將資料寫入登錄，以及載入*msvsmon.exe* （遠端偵錯工具），就可以提供這項服務而不需要寫入 HKEY_CLASSES_ROOT msvsmon 要註冊。 這會影響舊版的.NET 偵錯工具運算式評估工具或偵錯引擎設定為在載入*msvsmon.exe*程序。

## <a name="msvsmon-comclass-def"></a>msvsmon-comclass-def

若要使用這項技術，將 **.msvsmon-comclass-def.json* msvsmon 旁邊的檔案 (InstallDir:* \Common7\IDE\Remote Debugger\x64*)。

以下是範例 msvsmon-comclass-def 檔註冊管理和一個原生類別：

檔案名稱：*MyCompany.MyExample.msvsmon-comclass-def.json*

```json
{
  "managedCOMClasses": [
    {
      "clsid": "{C9F48B25-36ED-4B22-8210-98BC5BE4D1E7}",
      "assemblyName": "MyCompany.MyAssembly",
      "className": "MyCompany.MyNamespace.MyClass"
    }
  ],
  "nativeCOMClasses": [
    {
      "clsid": "{42A476E9-8FA7-44D5-ADFE-216AD371EEC9}",
      "dllPath": "MyExample.dll"
    }
  ]
}
```

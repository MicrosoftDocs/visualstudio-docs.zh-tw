---
title: 遷移64位偵錯工具 COM 類別註冊 |Microsoft Docs
ms.date: 11/10/2016
ms.topic: conceptual
ms.assetid: 45cfcee6-7a68-4d4f-b3f6-e2d8a0fa066a
author: gregg-miskelly
ms.author: greggm
manager: jillfra
ms.workload:
- greggm
ms.openlocfilehash: 74fbb959f8272be001aad8a576724d5eb1ad6157
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "62433691"
---
# <a name="migrate-64-bit-debugger-com-class-registration"></a>遷移64位偵錯工具 COM 類別註冊

針對在 HKEY_CLASSES_ROOT 中使用 regasm、regsvr32 或直接寫入登錄並載入至 *msvsmon.exe* (遠端偵錯程式) 的偵錯工具擴充功能，現在可以將此註冊提供給 msvsmon，而不需要寫入至 HKEY_CLASSES_ROOT。 這會影響舊版 .NET 偵錯工具運算式評估工具或設定為在 *msvsmon.exe* 進程中載入的偵錯工具引擎。

## <a name="msvsmon-comclass-def"></a>msvsmon-comclass.zip-def

若要使用這項技術，請 ** 在* msvsmon (InstallDir：* \Common7\IDE\Remote Debugger\x64 * ) 旁的檔案上新增.msvsmon-comclass-def.js。

以下是一個範例 msvsmon-comclass.zip .def 檔案，其會註冊一個 managed 和一個原生類別：

檔案名： *MyCompany.MyExample.msvsmon-comclass-def.js開啟*

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

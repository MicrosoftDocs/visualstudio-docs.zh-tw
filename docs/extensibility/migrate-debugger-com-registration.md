---
title: "移轉 64 位元偵錯工具 COM 類別註冊 |Microsoft 文件"
ms.custom: 
ms.date: 11/10/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 45cfcee6-7a68-4d4f-b3f6-e2d8a0fa066a
caps.latest.revision: "1"
author: gregg-miskelly
ms.author: greggm
manager: ghogen
ms.workload: greggm
ms.openlocfilehash: 737c970555fce8f3cdac118421eddb09f52d7c53
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="migrate-64-bit-debugger-com-class-registration"></a>移轉 COM 類別註冊 64 位元偵錯工具

偵錯工具擴充功能的註冊 HKEY_CLASSES_ROOT 中的 COM 類別 （透過使用 regasm，regsvr32，或直接寫入登錄），並載入 msvsmon.exe （遠端偵錯工具），您就可以不需要提供此註冊要 msvsmon要寫入 HKEY_CLASSES_ROOT。 這會影響舊版的.NET 偵錯工具運算式評估工具或已設定為 msvsmon.exe 處理序中載入的偵錯引擎。

## <a name="msvsmon-comclass-def"></a>msvsmon-comclass def

若要使用這項技術，加入 *.msvsmon-comclass-def.json 檔案旁邊 msvsmon (InstallDir:\Common7\IDE\Remote Debugger\x64)。

以下是範例 msvsmon-comclass def 檔註冊其中一個受管理和一個原生類別：

檔案名稱： MyCompany.MyExample.msvsmon comclass def.json

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

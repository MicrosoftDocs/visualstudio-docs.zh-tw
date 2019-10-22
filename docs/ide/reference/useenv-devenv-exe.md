---
title: -UseEnv (devenv.exe)
ms.date: 01/10/2019
ms.topic: reference
f1_keywords:
- VC.Project.UseEnvVars.ExcludePath
- VC.Project.UseEnvVars.LibraryPath
- VC.Project.UseEnvVars.SourcePath
- VC.Project.UseEnvVars.Include
- VC.Project.UseEnvVars.Path
- VC.Project.UseEnvVars.ReferencePath
helpviewer_keywords:
- UseEnv switch
- /UseEnv Devenv switch
- Devenv, /UseEnv
ms.assetid: 2dd14603-a61b-42d2-ba31-427a0ee8a799
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: da7a5e1d3490ea8342e6a7b21e91552ae2e8fdf0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72622399"
---
# <a name="useenv-devenvexe"></a>/UseEnv (devenv.exe)

啟動 Visual Studio，並載入特定環境變數進行編譯。

> [!NOTE]
> 此參數的安裝包含 **使用 C++ 的桌面開發**工作負載。

## <a name="syntax"></a>語法

```shell
devenv /UseEnv {SolutionName|ProjectName}
```

## <a name="arguments"></a>引數

- *SolutionName*

  解決方案檔的完整路徑和名稱。

- *ProjectName*

  專案檔的完整路徑和名稱。

## <a name="remarks"></a>備註

此參數會影響專案屬性中適用於 **VC++ 目錄**的 Visual Studio IDE。 如果您指定 `/UseEnv` 參數，[VC++ 目錄] 節點會顯示 PATH、INCLUDE、LIBPATH 和 LIB 環境變數的值 （它也會顯示 [**來原始目錄**] 和 [**排除目錄**] 的值）。否則，節點會將環境變數取代為五個目錄值：**可執行檔目錄**、 **Include 目錄**、**參考目錄**、連結**庫目錄**，以及連結**庫 WinRT 目錄**。

> [!TIP]
> 您可以使用滑鼠右鍵按一下 C++ 專案，然後選取 [屬性] 來存取專案屬性。 在 [屬性頁] 對話方塊中，依序選取 [組態屬性] 和 [VC++ 目錄]。

使用此參數指定專案名稱時，工具會顯示專案父代方案內所有專案的環境變數。

## <a name="example"></a>範例

下列範例會啟動 Visual Studio，並將環境變數載入到 `MySolution` 方案的屬性頁。

```shell
devenv.exe /useenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln"
```

## <a name="see-also"></a>請參閱

- [Devenv 命令列參數](../../ide/reference/devenv-command-line-switches.md)
- [VC++ 目錄屬性頁 (Windows)](/cpp/build/reference/vcpp-directories-property-page)

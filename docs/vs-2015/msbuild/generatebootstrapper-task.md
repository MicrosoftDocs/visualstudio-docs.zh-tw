---
title: GenerateBootstrapper 工作 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GenerateBootstrapper
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, GenerateBootstrapper task
- GenerateBootstrapper task [MSBuild]
ms.assetid: ca3ba2c6-d2ea-41f2-b7e3-0fc2b0730460
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 488caf02a20b4f0855df1ba2ef64c85e70e1a6a4
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/17/2019
ms.locfileid: "59668115"
---
# <a name="generatebootstrapper-task"></a>GenerateBootstrapper 工作
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

提供自動化方式來偵測、下載及安裝應用程式及其必要條件。 它可用來做為單一安裝程式，針對組成應用程式的所有元件整合個別的安裝程式。  
  
## <a name="task-parameters"></a>工作參數  
 下表說明 `GenerateBootstrapper` 工作的參數。  
  
- `ApplicationFile`  
  
   選擇性的 `String` 參數。  
  
   指定啟動載入器將用來在安裝所有必要條件之後開始安裝應用程式的檔案。 如果未指定 `BootstrapperItems` 和 `ApplicationFile` 參數，將會產生建置錯誤。  
  
- `ApplicationName`  
  
   選擇性的 `String` 參數。  
  
   指定啟動載入器將安裝的應用程式名稱。 此名稱將在安裝期間出現於啟動載入器所使用的 UI 中。  
  
- `ApplicationRequiresElevation`  
  
   選擇性的 `Boolean` 參數。  
  
   如果是 `true`，則在目標電腦上安裝元件時，該元件會以更高的權限來執行。  
  
- `ApplicationUrl`  
  
   選擇性的 `String` 參數。  
  
   指定裝載應用程式安裝程式的 Web 位置。  
  
- `BootstrapperComponentFiles`  
  
   選擇性的 `String[]` 輸出參數。  
  
   指定啟動載入器封裝檔案的建置位置。  
  
- `BootstrapperItems`  
  
   選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。  
  
   指定要在啟動載入器內建置的產品。 傳遞給此參數的項目應具有下列語法：  
  
  ```  
  <BootstrapperItem  
      Include="ProductCode">  
      <ProductName>  
          ProductName  
      </ProductName>  
  </BootstrapperItem>  
  ```  
  
   `Include` 屬性可用來表示必須安裝的必要條件名稱。 `ProductName` 項目中繼資料是選擇性的，而且萬一找不到封裝，建置引擎將使用它做為易記名稱。 除非未指定 `ApplicationFile`，否則這些項目不是必要的 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 輸入參數。 您應該基於每個必須針對您應用程式安裝的必要條件包含一個項目。  
  
   如果未指定 `BootstrapperItems` 和 `ApplicationFile` 參數，將會產生建置錯誤。  
  
- `BootstrapperKeyFile`  
  
   選擇性的 `String` 輸出參數。  
  
   指定 setup.exe 的建置位置  
  
- `ComponentsLocation`  
  
   選擇性的 `String` 參數。  
  
   指定啟動載入器用來尋找要安裝之安裝必要條件的位置。 此參數的值如下：  
  
  - `HomeSite`：表示必要條件已由元件廠商所裝載。  
  
  - `Relative`：表示必要條件位於應用程式相同的位置。  
  
  - `Absolute`：表示可在集中式 URL 中找到所有元件。 此值應該與 `ComponentsUrl` 輸入參數搭配使用。  
  
    如果未指定 `ComponentsLocation`，預設會使用 `HomeSite`。  
  
- `ComponentsUrl`  
  
   選擇性的 `String` 參數。  
  
   指定包含安裝必要條件的 URL。  
  
- `CopyComponents`  
  
   選擇性的 `Boolean` 參數。  
  
   如果是 `true`，啟動載入器會將所有輸出檔案複製到 `OutputPath` 參數中指定的路徑。 `BootstrapperComponentFiles` 參數的值全部都應以此路徑為依據。 如果是 `false`，不會複製檔案，而 `BootstrapperComponentFiles` 值會以 `Path` 參數的值為依據。  此參數的預設值為 `true`。  
  
- `Culture`  
  
   選擇性的 `String` 參數。  
  
   指定用於啟動載入器 UI 和安裝必要條件的文化特性。 無法使用指定的文化特性時，工作會使用 `FallbackCulture` 參數的值。  
  
- `FallbackCulture`  
  
   選擇性的 `String` 參數。  
  
   指定用於啟動載入器 UI 和安裝必要條件的次要文化特性。  
  
- `OutputPath`  
  
   選擇性的 `String` 參數。  
  
   指定要複製 setup.exe 和所有封裝檔案的位置。  
  
- `Path`  
  
   選擇性的 `String` 參數。  
  
   指定所有可用必要條件封裝的位置。  
  
- `SupportUrl`  
  
   選擇性的 `String` 參數。  
  
   指定應在啟動載入器安裝失敗時提供的 URL  
  
- `Validate`  
  
   選擇性的 `Boolean` 參數。  
  
   如果是 `true`，啟動載入器會在指定的輸入啟動載入器項目上執行 XSD 驗證。 此參數的預設值為 `false`。  
  
## <a name="remarks"></a>備註  
 除了上述所列的參數，此項工作還會繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。 如需這些其他參數的清單及其說明，請參閱 [TaskExtension Base Class](../msbuild/taskextension-base-class.md)。  
  
## <a name="example"></a>範例  
 下列範例會使用 `GenerateBootstrapper` 工作，來安裝必須安裝 [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] 做為必要條件的應用程式。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <BootstrapperFile Include="Microsoft.Net.Framework.2.0">  
            <ProductName>Microsoft .NET Framework 2.0</ProductName>  
        </BootstrapperFile>  
    </ItemGroup>  
  
    <Target Name="BuildBootstrapper">  
        <GenerateBootstrapper  
            ApplicationFile="WindowsApplication1.application"  
            ApplicationName="WindowsApplication1"  
            ApplicationUrl="http://mycomputer"  
            BootstrapperItems="@(BootstrapperFile)"  
            OutputPath="C:\output" />  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>另請參閱  
 [工作](../msbuild/msbuild-tasks.md)   
 [工作參考](../msbuild/msbuild-task-reference.md)

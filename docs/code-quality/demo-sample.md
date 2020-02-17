---
title: 用於程式碼分析的 C++ 專案範例
ms.date: 11/04/2016
ms.topic: sample
helpviewer_keywords:
- demo sample [Visual Studio ALM]
- code analysis, samples
ms.assetid: 09e1b9f7-5916-4ed6-a001-5c2d7e710682
author: corob-msft
ms.author: corob
manager: markl
ms.workload:
- multiple
ms.openlocfilehash: a7e06b29b4778bf2a9b1b327d015bb7eb12e8ec5
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/15/2020
ms.locfileid: "77271278"
---
# <a name="sample-c-project-for-code-analysis"></a>用於程式碼分析的 C++ 專案範例

下列程式示範如何建立[逐步解說：分析 C/C++程式碼是否有瑕疵](../code-quality/walkthrough-analyzing-c-cpp-code-for-defects.md)的範例。 這些程序會建立：

- A [！INCLUDEvsprvs] 名為 CppDemo 的方案。

- 名為 CodeDefects 的靜態程式庫專案。

- 名為 Annotations 的靜態程式庫專案。

這些程序也會提供標頭的程式碼，以及用於靜態程式庫的 *.cpp* 檔案。

## <a name="create-the-cppdemo-solution-and-the-codedefects-project"></a>建立 CppDemo 解決方案和 CodeDefects 專案

1. 開啟 [！INCLUDEvsprvs]，然後選取 [**建立新專案**]

2. 將語言篩選變更為**C++**

3. 選取 [**空專案**] 並按 **[下一步]**

4. 在 [**專案名稱**] 文字方塊中，輸入**CodeDefects**

5. 在 [**方案名稱**] 文字方塊中，輸入**CppDemo**

6. 按一下 [建立]

## <a name="configure-the-codedefects-project-as-a-static-library"></a>將 CodeDefects 專案設定為靜態程式庫

1. 在 [方案總管] 中，以滑鼠右鍵按一下 [CodeDefects]，然後按一下 [屬性]。

2. 展開 [組態屬性]，然後按一下 [一般]。

3. 在 [**一般**] 清單中，將 [設定**類型**] 變更為 [**靜態程式庫（.lib）** ]。

4. 在 [ **Advanced** ] 清單中，將 [**目標副檔名**] 變更為 **.lib**

## <a name="add-the-header-and-source-file-to-the-codedefects-project"></a>將標頭和來源檔案新增至 CodeDefects 專案

1. 在 [方案總管] 中，展開 [CodeDefects]，以滑鼠右鍵按一下 [標頭檔]，按一下 [新增]，然後按一下 [新增項目]。

2. 在 [新增項目] 對話方塊中，按一下 [程式碼]，然後按一下 [標頭檔 (.h)]。

3. 在 [名稱] 方塊中，鍵入 **Bug.h**，然後按一下 [新增]。

4. 複製下列程式碼，並將它貼入編輯器中的*錯誤 .h*檔案。

```cpp
#pragma once

#include <windows.h>

// These functions are consumed by the sample
// but are not defined. This project cannot be linked!
bool CheckDomain(LPCTSTR);
HRESULT ReadUserAccount();

// These constants define the common sizes of the
// user account information throughout the program
const int USER_ACCOUNT_LEN = 256;
const int ACCOUNT_DOMAIN_LEN = 128;
```

5. 在 [方案總管] 中，以滑鼠右鍵按一下 [來源檔案]，指向 [新增]，然後按一下 [新增項目]。

6. 在 [新增項目] 對話方塊中，按一下 [C++ 檔案 (.cpp)]

7. 在 [名稱] 方塊中，鍵入 **Bug.cpp**，然後按一下 [新增]。

8. 複製下列程式碼，並將它貼入編輯器中的*錯誤 .cpp*檔案。

```cpp
#include "Bug.h"

// the user account
TCHAR g_userAccount[USER_ACCOUNT_LEN] = {};
int len = 0;

bool ProcessDomain()
{
    TCHAR* domain = new TCHAR[ACCOUNT_DOMAIN_LEN];
    // ReadUserAccount gets a 'domain\user' input from
    //the user into the global 'g_userAccount'
    if (ReadUserAccount())
    {
        // Copies part of the string prior to the '\'
        // character onto the 'domain' buffer
        for (len = 0; (len < ACCOUNT_DOMAIN_LEN) && (g_userAccount[len] != L'\0'); len++)
        {
            if (g_userAccount[len] == '\\')
            {
                // Stops copying on the domain and user separator ('\')
                break;
            }
            domain[len] = g_userAccount[len];
        }
        if ((len = ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != '\\'))
        {
            // '\' was not found. Invalid domain\user string.
            delete[] domain;
            return false;
        }
        else
        {
            domain[len] = '\0';
        }
        // Process domain string
        bool result = CheckDomain(domain);

        delete[] domain;
        return result;
    }
    return false;
}

int path_dependent(int n)
{
    int i;
    int j;
    if (n == 0)
        i = 1;
    else
        j = 1;
    return i + j;
}
```

9. 按一下 [檔案] 功能表，然後按一下 [全部儲存]。

## <a name="add-the-annotations-project-and-configure-it-as-a-static-library"></a>新增 Annotations 專案並將其設定為靜態程式庫

1. 在 [方案總管] 中，按一下 [CppDemo]，指向 [新增]，然後按一下 [新增專案]。

2. 在 [新增**專案**] 對話方塊中，將 [語言篩選] **C++** 變更為，然後選取 [**空白專案**]，然後按 **[下一步]** 。

3. 在 [**專案名稱**] 文字方塊中，輸入**批註**，然後按一下 [**建立**]。

4. 在 [方案總管] 中，以滑鼠右鍵按一下 [Annotations]，然後按一下 [屬性]。

5. 展開 [組態屬性]，然後按一下 [一般]。

6. 在 [**一般**] 清單中，將 [設定**類型**] 變更為，然後按一下 [**靜態程式庫（.lib）** ]。

7. 在 [ **Advanced** ] 清單中，選取 [**目標檔案副檔名**] 旁邊的資料行中的文字，然後輸入 **.lib**。


## <a name="add-the-header-file-and-source-file-to-the-annotations-project"></a>將標頭檔和來源檔案新增至 Annotations 專案

1. 在 [方案總管] 中，展開 [Annotations]，以滑鼠右鍵按一下 [標頭檔]，按一下 [新增]，然後按一下 [新增項目]。

2. 在 [新增項目] 對話方塊中，按一下 [標頭檔 (.h)]。

3. 在 [名稱] 方塊中，鍵入 **annotations.h**，然後按一下 [新增]。

4. 複製下列程式碼，並將它貼到編輯器中的 [ *.h* ] 檔案。

```cpp
#pragma once
#include <sal.h>

struct LinkedList
{
    struct LinkedList* next;
    int data;
};

typedef struct LinkedList LinkedList;

_Ret_maybenull_ LinkedList* AllocateNode();
```

5. 在 [方案總管] 中，以滑鼠右鍵按一下 [來源檔案]，指向 [新增]，然後按一下 [新增項目]。

6. 在 [新增項目] 對話方塊中，按一下 [程式碼]，然後按一下 [C++ 檔案 (.cpp)]

7. 在 [名稱] 方塊中，鍵入 **annotations.cpp**，然後按一下 [新增]。

8. 複製下列程式碼，並將它貼到編輯器中的*注釋 .cpp*檔案。

```cpp
#include "annotations.h"

LinkedList* AddTail(LinkedList* node, int value)
{
    // finds the last node
    while (node->next != nullptr)
    {
        node = node->next;
    }

    // appends the new node
    LinkedList* newNode = AllocateNode();
    newNode->data = value;
    newNode->next = 0;
    node->next = newNode;

    return newNode;
}
```

9. 按一下 [檔案] 功能表，然後按一下 [全部儲存]。


解決方案現在已完成，應建立而不會發生錯誤。

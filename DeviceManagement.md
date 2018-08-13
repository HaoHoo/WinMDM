
# 基于Windows 10 MDM的设备管理

## 1. 系统菜单CSP


## 2. ADMX后向支持CSP

### 2.1 禁用所有USB存储设备


使用CDATA发送管理负载
<![CDATA[ ]]>

```XML
<Replace>
  <CmdID>c93bd3ae-46ae-435c-86b7-fb5e60791924</CmdID>
  <Item>
    <Target>
        <LocURI>./Device/Vendor/MSFT/Policy/Config/DeviceInstallation/PreventInstallationOfMatchingDeviceIDs</LocURI>
    </Target>
    <Meta>
      <Format xmlns="syncml:metinf">chr</Format>
      <Type>text/plain</Type>
    </Meta>
      <Data><![CDATA[<enabled/><data id="DeviceInstall_IDs_Deny_Retroactive" value="true"/><Data id="DeviceInstall_IDs_Deny_List" value="1USB\Class_08"/>]]>
    </Data>
  </Item>
</Replace>
```

使用XML编码管理负载
```XML
<Replace>
  <CmdID>a04b8405-0948-4c5c-8bfd-c844df8b08a2</CmdID>
  <Item>
    <Target>
      <LocURI>./Device/Vendor/MSFT/Policy/Config/DeviceInstallation/PreventInstallationOfMatchingDeviceIDs</LocURI>
    </Target>
    <Meta>
      <Format>chr</Format>
      <Type>text/plain</Type>
    </Meta>
    <Data>
      &lt;enabled/&gt;&lt;data id=&quot;DeviceInstall_IDs_Deny_Retroactive&quot; value=&quot;true&quot;/&gt;&lt;Data id=&quot;DeviceInstall_IDs_Deny_List&quot; value=&quot;1&#xF000;USB\Class_08&quot;/&gt;
    </Data>
  </Item>
</Replace>
```

### 2.2 仅禁用USB磁盘
本示例仅禁用USB磁盘类存储设备，例如U盘、一类读卡器、移动移动硬盘等等。

```XML
<Replace>
  <CmdID>c93bd3ae-46ae-435c-86b7-fb5e60791924</CmdID>
  <Item>
    <Target>
        <LocURI>./Device/Vendor/MSFT/Policy/Config/DeviceInstallation/PreventInstallationOfMatchingDeviceIDs</LocURI>
    </Target>
    <Meta>
      <Format xmlns="syncml:metinf">chr</Format>
      <Type>text/plain</Type>
    </Meta>
      <Data><![CDATA[<enabled/><data id="DeviceInstall_IDs_Deny_Retroactive" value="true"/><Data id="DeviceInstall_IDs_Deny_List" value="1USB\Class_08&SubClass_6"/>]]>
    </Data>
  </Item>
</Replace>
```
?测试时发现手动配置注册表没问题，策略推送没成功，有待找个新的VM验证
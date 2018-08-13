# 基于Windows 10 MDM的应用管理

## Office安装CSP

### Office的安装和配置方法

Office 2016的配置文件

```XML
<Configuration>
  <Add OfficeClientEdition="32" Channel="Current">
    <Product ID="O365BusinessRetail">
      <Language ID="en-us" />
      <Language ID="zh-cn" />
    </Product>
  </Add>
  <Display Level="None" AcceptEULA="TRUE" />
</Configuration>
```

配置项非常多，这里的例子是安装O365，不显示接受许可的界面，同时安装中英文界面等。

如果需要借助MDM的框架，利用CSP推送管理负载，就需要对Office 2016的配置文件进行XML编码。

```XML
<SyncML xmlns="SYNCML:SYNCML1.2">
  <SyncBody>
    <Exec>
      <CmdID>7</CmdID>
        <Item>
          <Target>
            <LocURI>./Vendor/MSFT/Office/Installation/0AA79349-F334-4859-96E8-B4AB43E9FEA0/install</LocURI>
          </Target>
          <Meta>
            <Format xmlns="syncml:metinf">chr</Format>
          </Meta> 
          <Data>
            &lt;Configuration&gt;&lt;Add OfficeClientEdition=&quot;32&quot; Channel=&quot;Current&quot;&gt;&lt;Product ID=&quot;O365BusinessRetail&quot;&gt;&lt;Language ID=&quot;en-us&quot; /&gt;&lt;Language ID=&quot;zh-cn&quot; /&gt;&lt;/Product&gt;&lt;/Add&gt;&lt;Display Level=&quot;None&quot; AcceptEULA=&quot;TRUE&quot; /&gt;&lt;/Configuration&gt;
          </Data>
        </Item>
    </Exec>
    <Final/>
  </SyncBody>
</SyncML>
```

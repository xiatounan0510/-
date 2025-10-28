 -graph TB
    %% 参与者
    PAT1[未注册用户]
    PAT2[注册用户]
    PAT3[系统管理员]
    PAT4[挂号处工作人员]
    PAT5[分诊台护士]
    PAT6((第三方支付系统))
    
    %% 用例 - 使用不同形状区分类型
    subgraph 医院预约挂号系统
        %% 查询类用例 - 椭圆形
        UC1[查询医院信息]
        
        %% 用户管理类用例 - 圆角矩形
        UC2[用户注册]
        UC3[用户登录]
        UC4[审核用户注册]
        UC5[信用等级管理]
        
        %% 预约核心业务 - 矩形
        UC6[预约挂号]
        UC7[取消预约]
        UC8[在线支付]
        UC9[打印预约单/挂号单]
        
        %% 排班管理 - 六边形
        UC10[维护医生排班]
        UC11[自动生成出诊计划]
        UC12[系统规则设置]
        
        %% 现场业务 - 平行四边形
        UC13[分诊确认]
        UC14[现场取消预约]
        UC15[现场收费]
    end
    
    %% 参与者与用例关系
    PAT1 --> UC1
    PAT1 --> UC2
    
    PAT2 --> UC1
    PAT2 --> UC3
    PAT2 --> UC6
    PAT2 --> UC7
    PAT2 --> UC8
    PAT2 --> UC9
    
    PAT3 --> UC4
    PAT3 --> UC5
    PAT3 --> UC10
    PAT3 --> UC11
    PAT3 --> UC12
    
    PAT4 --> UC14
    PAT4 --> UC15
    
    PAT5 --> UC13
    
    PAT6 -.-> UC8
    
    %% 包含关系
    UC2 --> UC4
    UC6 --> UC8
    UC10 --> UC11
    UC12 --> UC11
    
    %% 扩展关系
    UC7 -.-> UC8
    UC7 -.-> UC5
    
    %% 样式设置
    classDef participant fill:#e1f5fe,stroke:#01579b,stroke-width:2px
    classDef query fill:#bbdefb,stroke:#1976d2
    classDef userMgmt fill:#c8e6c9,stroke:#388e3c
    classDef booking fill:#fff9c4,stroke:#f57f17
    classDef schedule fill:#d1c4e9,stroke:#7b1fa2
    classDef onsite fill:#ffccbc,stroke:#e64a19
    classDef external fill:#e0f2f1,stroke:#00695c,stroke-dasharray: 5 5
    
    class PAT1,PAT2,PAT3,PAT4,PAT5 participant
    class PAT6 external
    class UC1 query
    class UC2,UC3,UC4,UC5 userMgmt
    class UC6,UC7,UC8,UC9 booking
    class UC10,UC11,UC12 schedule
    class UC13,UC14,UC15 onsite

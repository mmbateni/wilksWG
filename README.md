## wilksWG
##wilksWG implements the Wilks Multisite Weather Generator for precipitation series, based on the work of D.S.Wilks, see 
##[[Wilks, 1998]](https://www.sciencedirect.com/science/article/pii/S0022169498001863?via%3Dihub)
graph LR
    %% Work Packages (Main Structure)
    WP1[WP1: Dual-Path Computational Architecture]:::wp
    WP2[WP2: HEC-RAS 2D Hydraulic Modeling]:::wp
    WP3[WP3: AI Model Fine-Tuning & Validation]:::wp
    
    %% Critical Tasks (Simplified)
    T11[Task 1.1: Training Path]:::task
    T12[Task 1.2: Operational Path]:::task
    T22[Task 2.2: Calibration]:::task
    T32[Task 3.2: Model Refinement]:::task
    
    %% Key Inputs/Outputs
    Historical[Historical Data\n(ECMWF/LiDAR/XGBoost)]:::data
    RealTime[Real-Time Data\n(ECMWF/Sentinel-1)]:::data
    Dashboards[Stakeholder Dashboards]:::output
    
    %% Core Workflow
    Historical --> T11
    T11 -->|Ground Truth| T32
    RealTime --> T12
    T12 --> Dashboards
    
    WP2 --> T22
    T22 -->|Calibrated Model| T32
    T32 -->|Refined AI| T12
    
    %% Grouping
    WP1 --> T11 & T12
    WP2 --> T22
    WP3 --> T32
    
    %% Styling
    classDef wp fill:#1890ff,stroke:#096dd9,color:white,font-weight:bold;
    classDef task fill:#ffffff,stroke:#333,stroke-width:1.5px;
    classDef data fill:#e6f7ff,stroke:#91d5ff;
    classDef output fill:#ffe58f,stroke:#ffd591;

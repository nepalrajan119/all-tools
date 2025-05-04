
    body {
        background-color: #f5f7fa;
        margin: 0;
        padding: 20px;
        color: #333;
    }
    
    .container {
        max-width: 800px;
        margin: 0 auto;
        background-color: white;
        border-radius: 15px;
        box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
        padding: 30px;
    }
    
    h1 {
        text-align: center;
        color: #4a6bdf;
        margin-bottom: 30px;
        font-size: 28px;
    }
    
    .input-section {
        display: flex;
        flex-wrap: wrap;
        gap: 20px;
        margin-bottom: 30px;
    }
    
    .input-group {
        flex: 1;
        min-width: 200px;
    }
    
    label {
        display: block;
        margin-bottom: 8px;
        font-weight: 600;
        color: #555;
    }
    
    input[type="number"] {
        width: 100%;
        padding: 12px 15px;
        border: 2px solid #e0e3e9;
        border-radius: 8px;
        font-size: 16px;
        transition: border-color 0.3s;
    }
    
    input[type="number"]:focus {
        border-color: #4a6bdf;
        outline: none;
    }
    
    .range-container {
        margin-top: 10px;
        display: flex;
        align-items: center;
        gap: 10px;
    }
    
    input[type="range"] {
        flex: 1;
        height: 8px;
        -webkit-appearance: none;
        background: #e0e3e9;
        border-radius: 5px;
    }
    
    input[type="range"]::-webkit-slider-thumb {
        -webkit-appearance: none;
        width: 20px;
        height: 20px;
        background: #4a6bdf;
        border-radius: 50%;
        cursor: pointer;
    }
    
    .calculate-btn {
        background-color: #4a6bdf;
        color: white;
        border: none;
        padding: 14px 25px;
        font-size: 16px;
        font-weight: 600;
        border-radius: 8px;
        cursor: pointer;
        display: block;
        margin: 0 auto;
        transition: background-color 0.3s;
    }
    
    .calculate-btn:hover {
        background-color: #3a5ad1;
    }
    
    .results {
        margin-top: 40px;
        display: none;
    }
    
    .results h2 {
        text-align: center;
        color: #4a6bdf;
        margin-bottom: 20px;
    }
    
    table {
        width: 100%;
        border-collapse: collapse;
        margin-top: 20px;
        background-color: white;
        border-radius: 10px;
        overflow: hidden;
        box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
    }
    
    th, td {
        padding: 15px;
        text-align: left;
        border-bottom: 1px solid #f0f0f0;
    }
    
    th {
        background-color: #f8f9fd;
        font-weight: 600;
        color: #4a6bdf;
    }
    
    tr:hover {
        background-color: #f8f9fd;
    }
    
    .highlight {
        font-weight: 700;
        color: #4a6bdf;
    }
    
    .emoji {
        font-size: 20px;
        margin-right: 8px;
        vertical-align: middle;
    }
    
    @media (max-width: 600px) {
        .container {
            padding: 20px;
        }
        
        .input-group {
            min-width: 100%;
        }
        
        th, td {
            padding: 10px;
            font-size: 14px;
        }
    }
</style>

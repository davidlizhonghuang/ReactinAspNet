### React CORS 

##Asp.net Web API 

  public class OrdersController : Controller
    {
        private OrderEntities db = new OrderEntities();
        // GET: Orders
        [EnableCors(origins: "*", headers: "*", methods: "*")]
        public async Task<ActionResult> Index()
        {
            return View(await db.Orders.ToListAsync());
        }
...
    }
 
 enable cors
 
  public static class WebApiConfig
    {
        public static void Register(HttpConfiguration config)
        {
            // Web API configuration and services

            var cors = new EnableCorsAttribute("localhost", "*", "*");

            config.EnableCors(cors);
            ...
            
    }
    
    Nuget package
    
  <package id="Microsoft.AspNet.WebApi.Core" version="5.2.7" targetFramework="net472" />
  <package id="Microsoft.AspNet.WebApi.Cors" version="5.2.7" targetFramework="net472" />
  
  
  API is ready to go
  
## React UI

asp.net core client -React

  <TargetFramework>netcoreapp2.1</TargetFramework>
    <TypeScriptCompileBlocked>true</TypeScriptCompileBlocked>
    <TypeScriptToolsVersion>Latest</TypeScriptToolsVersion>
    <IsPackable>false</IsPackable>
  <SpaRoot>ClientApp\</SpaRoot>
    
now we can add clientApp via React npm

we create a component to consume third party API

import React from 'react';
import EditOrder from './editorder';
import axios from 'axios';

class EditData extends React.Component {
    constructor() {
        super();
        this.state = {data: []};
    }

    render() {

        axios.defaults.baseURL = 'http://localhost:44327';
        axios.defaults.headers.post['Content-Type'] = 'application/json;charset=utf-8';
        axios.defaults.headers.post['Access-Control-Allow-Origin'] = '*';
        
       axios.get("https://localhost:44372/Orders/Details/2")
            .then((resd) => {
                this.setState = { data: resd };
                console.log(resd.data);
            }).catch();

        return this.state.data;
}

export default EditData;


## React can retrieve data from cross domain




 


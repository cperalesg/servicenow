function onLoad() {

    //Populate the variables with the parameters passed in the URL
    //Use the 'getParameterValue' function below to get the parameter values from the URL

    //Get Vaccine Set and Immunisation Provider values from URL
    var vaccineSet = getParameterValue('sysparm_vaccine_set');
    var immunisationProvider = getParameterValue('sysparm_immunisation_provider');
    var clinic = getParameterValue('sysparm_clinic');
    var event = getParameterValue('sysparm_event');

    //Set Vaccine Set value into form variable
    if (vaccineSet) {
        g_form.setValue('vaccine_set', vaccineSet);
    }

    //Set Immunisation Provider value into form variable
    if (immunisationProvider) {
        g_form.setValue('immunisation_provider', immunisationProvider);
    }

    //Set Clinic value into form variable
    if (clinic) {
        g_form.setValue('clinic', clinic);
    }

    //Set Event value into form variable
    if (event) {
        g_form.setValue('event_number', event);
    }
	
    //Call async script include to get Clinic and User details
    var clinicDetails = new GlideAjax('ClinicDetailsUtil');
    clinicDetails.addParam('sysparm_name', 'getClinicDetails');
    clinicDetails.addParam('sysparm_clinicSelect', clinic);
    clinicDetails.addParam('sysparm_immunisationProviderSelect', immunisationProvider);
	
    clinicDetails.getXMLAnswer(function(response) {
        var clinicObj = JSON.parse(response);

        //Set form variables from script include response
		g_form.setValue('address', clinicObj.street);
        g_form.setValue('postcode', clinicObj.postcode);
        g_form.setValue('state', clinicObj.state);
        g_form.setValue('phone', clinicObj.phone);
		g_form.setValue('immunisation_provider_id', clinicObj.id);
		
        //g_form.setValue('email', clinicObj.email);
    });

}

function getParameterValue(name) {  
    name = name.replace(/[\[]/, "\\\[").replace(/[\]]/, "\\\]");  
    var regexS = "[\\?&]" + name + "=([^&#]*)";  
    var regex = new RegExp(regexS);  
    var results = regex.exec(top.location);  
    if (results == null) {  
        return "";  
    } else {  
        return unescape(results[1]);  
    }  

}

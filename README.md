# welcomemessage

The welcome message should appear only once to the new registration. Instead of appear everytime login 

$(document).ready(function() { 
  if($('body#challenge').length){
    if(document.referrer.indexOf('/register') !== -1){
      const encryptedUrl = window.btoa(new Date().getMinutes() + 1);
      $('.shopify-challenge__container > form').append('<input type="hidden" name="return_to" value="/account?user='+encryptedUrl+'">');
    }
  }
  
  if(window.location.href.indexOf('/account?user') !== -1) {
    const url = window.location.search.match(/\?user=(.*)/);

    const decrypted = window.atob(url[1]);

    if(parseInt(decrypted) >= new Date().getMinutes()) { 
      $('.WelcomeMessage').css('display', 'block');
    }
  }
});

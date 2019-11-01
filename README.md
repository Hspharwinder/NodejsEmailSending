# NodejsEmailSending

npm i nodemailer 

const nodemailer = require('nodemailer'); 

var sendEmail = async (data) => {
   // Generate test SMTP service account from ethereal.email 
   // Only needed if you don't have a real mail account for testing 
   let testAccount = await nodemailer.createTestAccount(); 
   // create reusable transporter object using the default SMTP transport 
   let transporter = nodemailer.createTransport({ 
        // Start :: uncomment this for testing 
          /* host: 'smtp.ethereal.email', port: 587, secure: false, 
          // true for 465, false for other ports */ 
        // End :: uncomment this for testing 
        service: "Gmail", 
        // comment this for test
         auth: { user: 'hspharwinder@gmail.com',  // generated ethereal user
               pass: process.env.PASSWORD // generated ethereal password
             } 
    }); 
    messageBody = '<h2>There is details of created new artist </h2>' + '<br>Name ::: ' + 
                    data.Name + '<br>Email ::: ' + 
                    data.Email + '<br>Phone No. ::: ' + 
                    data.MobileNo + '<br>Description ::: ' + 
                    data.Description; 
          
          // send mail with defined transport object 
          let info = await transporter.sendMail({ 
                                                  from: '<test@example.com>', // sender address 
                                                  to: 'uic.16mca8127@gmail.com, hspharwinder@gmail.com', // list of receivers 
                                                  subject: 'New Artist Created ✔',  // Subject line 
                                                  text: 'Detail of New Artist Created',  // plain text body
                                                  html: messageBody,  // html body 
                                                }); 
        console.log('Message sent: %s', info.messageId); 
        // Message sent: <b658f8ca-6296-ccf4-8306-87d57a0b4321@example.com> 
        // Preview only available when sending through an Ethereal account 
        console.log('Preview URL: %s', nodemailer.getTestMessageUrl(info)); 
        // Preview URL: https://ethereal.email/message/WaQKMgKddxQDoou... 
}

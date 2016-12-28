---
layout: post
title: HTTP Request Study Conclusion
date: 2016-01-20
categories: [PROGRAMMER_JAVA]
tags: [PROGRAMMER]

---

###HTTP request headers

* FORM DATA: results directly from user input and is sent as part of the URL for __GET__ requests and on a separate line for __POST__ requests.
* REQUEST HEADERS: indirectly set by the browser and are sent immediately following the initial __GET__ or __POST__ request line.

_the servlet needs to explicitly read the request headers to make use of this information:_ Accept, Accept-Encoding, Connection, Cookie, Host, Referer and User-Agent.

Understanding HTTP 1.1 Request Headers:

* Accept: This header specifies the MIME types that the browser or other clients can handle.
* Accept-Charset
* Accept-Encoding
* Accept-Language
* Authorization: This header is used by clients to identify themselves when accessing password-protected Web pages.
* Connection: This header indicates whether the client can handle persistent HTTP connec- tions.
* Content-Length: This header is applicable only to POST requests and gives the size of the POST data in bytes. 
* Cookie
* Host
* If-Modified-Since: This header indicates that the client wants the page only if it has been changed after the specified date.
* If-Unmodified-Since: This header is the reverse of If-Modified-Since; it specifies that the opera- tion should succeed only if the document is older than the specified date.
* Referer
* User-Agent: This header identifies the browser or other client making the request and can be used to return different content to different types of browsers.


###Sending compressed web pages.

###Changing the page according to how the user got there

	/** Servlet that displays referer-specific image. */	public class CustomizeImage extends HttpServlet 	{ 
		public void doGet(HttpServletRequest request,		HttpServletResponse response) 
			throws ServletException, IOException {			
			response.setContentType("text/html"); 
			PrintWriter out = response.getWriter();			String referer = request.getHeader("Referer");
			if (referer == null) {          		referer = "<I>none</I>";        	}			String title = "Referring page: " + referer; 			String imageName;			if (contains(referer, "JRun")) {          		imageName = "jrun-powered.gif";			} else if (contains(referer, "Resin")) { 
				imageName = "resin-powered.gif";			} else {				imageName = "tomcat-powered.gif";			}			String imagePath = "../request-headers/images/" + imageName;
			String docType ="<!DOCTYPE HTML PUBLIC \"-//W3C//DTD HTML 4.0 " + "Transitional//EN\">\n";    		out.println(docType +				"<HTML>\n" +				"<HEAD><TITLE>" + title + "</TITLE></HEAD>\n" + 
				"<BODY BGCOLOR=\"#FDF5E6\">\n" +				"<CENTER><H2>" + title + "</H2>\n" +				"<IMG SRC=\"" + imagePath + "\">\n" + "</CENTER></BODY></HTML>");		}
				private boolean contains(String mainString, String subString) {				return(mainString.indexOf(subString) != -1); 
		}	}
One certain html page:			<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.0 Transitional//EN"> <HTML><HEAD><TITLE>Referer Test</TITLE></HEAD>	<BODY BGCOLOR="#FDF5E6">	<H1 ALIGN="CENTER">Referer Test</H1>	Click <A HREF="/servlet/coreservlets.CustomizeImage">here</A> to visit the servlet.	</BODY></HTML>

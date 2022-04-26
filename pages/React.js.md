title:: React.js

- Download Components as pdf:
	- 1. Declare a certain area in your application that should be downloadable as PDF by using a React ref:
	  ```jsx
	  const App = () => {
	    const printRef = React.useRef();
	  
	    return (
	      <div>
	        <div>I will not be in the PDF.</div>
	        <div ref={printRef}>I will be in the PDF.</div>
	      </div>
	    );
	  };
	  ```
	- 2. Create a button with an event handler where you will implement the logic to download the part of the component as PDF:
	  ```jsx
	  const App = () => {
	    const printRef = React.useRef();
	  
	    const handleDownloadPdf = () => {
	      // TODO: logic
	    };
	  
	    return (
	      <div>
	        <button type="button" onClick={handleDownloadPdf}>
	          Download as PDF
	        </button>
	  
	        <div>I will not be in the PDF.</div>
	        <div ref={printRef}>I will be in the PDF.</div>
	      </div>
	    );
	  };
	  ```
	- 3. Install the libraries called [[html2canvas]] and [[jspdf]] via your command line:
	  ```bash
	  npm install html2canvas jspdf
	  ```
	- 4. Use the library to draw the component on a canvas, to transform it into an image, and finally to transform it into a PDF:
	  ```jsx
	  import html2canvas from 'html2canvas';
	  import { jsPDF } from 'jspdf';
	  
	  const App = () => {
	    const printRef = React.useRef();
	  
	    const handleDownloadPdf = async () => {
	      const element = printRef.current;
	      const canvas = await html2canvas(element);
	      const data = canvas.toDataURL('image/png');
	  
	      const pdf = new jsPDF();
	      const imgProperties = pdf.getImageProperties(data);
	      const pdfWidth = pdf.internal.pageSize.getWidth();
	      const pdfHeight =
	        (imgProperties.height * pdfWidth) / imgProperties.width;
	  
	      pdf.addImage(data, 'PNG', 0, 0, pdfWidth, pdfHeight);
	      pdf.save('print.pdf');
	    };
	  
	    return (
	      <div>
	        <button type="button" onClick={handleDownloadPdf}>
	          Download as PDF
	        </button>
	  
	        <div>I will not be in the PDF.</div>
	        <div ref={printRef}>I will be in the PDF.</div>
	      </div>
	    );
	  };
	  ```
-
-
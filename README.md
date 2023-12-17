# This is my local repo




package com.example.demo;
import com.itextpdf.text.Document;
import com.itextpdf.text.Paragraph;
import com.itextpdf.text.pdf.PdfContentByte;
import com.itextpdf.text.pdf.PdfWriter;
import com.itextpdf.text.pdf.PdfTemplate;
import org.jfree.chart.ChartFactory;
import org.jfree.chart.JFreeChart;
import org.jfree.data.general.DefaultPieDataset;
import java.awt.Graphics2D;
import java.awt.geom.Rectangle2D;
import java.io.FileOutputStream;

public class PieChartExample {

    private static JFreeChart createChart(String title, String product1, int value1, String product2, int value2, String product3, int value3) {
        DefaultPieDataset dataset = new DefaultPieDataset();
        dataset.setValue(product1, value1);
        dataset.setValue(product2, value2);
        dataset.setValue(product3, value3);

        return ChartFactory.createPieChart(
                title,
                dataset,
                true,
                true,
                false);
    }

    public static void createPdf(String filename) throws Exception {
        // Create a new PDF document
        Document document = new Document();
        PdfWriter writer = PdfWriter.getInstance(document, new FileOutputStream(filename));
        document.open();
        document.add(new Paragraph("Pie Chart Example"));
        document.newPage();
        // Create a PDF template with the size of the charts
        PdfContentByte contentByte = writer.getDirectContent();
        PdfTemplate template = contentByte.createTemplate(500, 500);
        Graphics2D graphics2d = template.createGraphics(500, 500);

        // Create the charts and draw them on the template
        JFreeChart chart1 = createChart("Product Sales 1", "Product1", 15, "Product2", 12, "Product3", 10);
        chart1.draw(graphics2d, new Rectangle2D.Double(250, 0, 200, 200));

        JFreeChart chart2 = createChart("Product Sales 2", "Product4", 20, "Product5", 18, "Product6", 22);
        chart2.draw(graphics2d, new Rectangle2D.Double(0, 0, 200, 200));

        JFreeChart chart3 = createChart("Product Sales 3", "Product7", 25, "Product8", 30, "Product9", 28);
        chart3.draw(graphics2d, new Rectangle2D.Double(150, 250, 200, 200));

        // Close the graphics object
        graphics2d.dispose();

        // Add the template to the document
        contentByte.addTemplate(template, 0, 0);

        // Close the PDF document
        document.close();
    }
}

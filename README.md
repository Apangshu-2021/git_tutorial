# This is my local repo
import org.jfree.chart.ChartFactory;
import org.jfree.chart.ChartPanel;
import org.jfree.chart.JFreeChart;
import org.jfree.data.general.DefaultPieDataset;
import javax.swing.*;

public class PieChartExample {

    private static ChartPanel createChartPanel(String title, String product1, int value1, String product2, int value2, String product3, int value3) {
        DefaultPieDataset dataset = new DefaultPieDataset();
        dataset.setValue(product1, value1);
        dataset.setValue(product2, value2);
        dataset.setValue(product3, value3);

        JFreeChart pieChart = ChartFactory.createPieChart(
                title,
                dataset,
                true, 
                true,
                false);

        return new ChartPanel(pieChart);
    }

    public static void main(String[] args) {
        JFrame frame = new JFrame();
        frame.setLayout(new BoxLayout(frame.getContentPane(), BoxLayout.Y_AXIS));
        frame.add(createChartPanel("Product Sales 1", "Product1", 15, "Product2", 12, "Product3", 10));
        frame.add(createChartPanel("Product Sales 2", "Product4", 20, "Product5", 18, "Product6", 22));
        frame.add(createChartPanel("Product Sales 3", "Product7", 25, "Product8", 30, "Product9", 35));
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        frame.pack();
        frame.setVisible(true);
    }
}

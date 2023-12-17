# This is my local repo

import org.jfree.chart.ChartFactory;
import org.jfree.chart.ChartPanel;
import org.jfree.chart.JFreeChart;
import org.jfree.data.general.DefaultPieDataset;
import javax.swing.*;

public class PieChartExample extends JFrame {

    public PieChartExample() {
        setLayout(new BoxLayout(getContentPane(), BoxLayout.Y_AXIS));

        // PieChart 1
        DefaultPieDataset dataset1 = new DefaultPieDataset();
        dataset1.setValue("Product1", 15);
        dataset1.setValue("Product2", 12);
        dataset1.setValue("Product3", 10);

        JFreeChart pieChart1 = ChartFactory.createPieChart(
                "Product Sales 1",
                dataset1,
                true, 
                true,
                false);

        ChartPanel chartPanel1 = new ChartPanel(pieChart1);
        add(chartPanel1);

        // PieChart 2
        DefaultPieDataset dataset2 = new DefaultPieDataset();
        dataset2.setValue("Product4", 20);
        dataset2.setValue("Product5", 18);
        dataset2.setValue("Product6", 22);

        JFreeChart pieChart2 = ChartFactory.createPieChart(
                "Product Sales 2",
                dataset2,
                true, 
                true,
                false);

        ChartPanel chartPanel2 = new ChartPanel(pieChart2);
        add(chartPanel2);

        // PieChart 3
        DefaultPieDataset dataset3 = new DefaultPieDataset();
        dataset3.setValue("Product7", 25);
        dataset3.setValue("Product8", 30);
        dataset3.setValue("Product9", 35);

        JFreeChart pieChart3 = ChartFactory.createPieChart(
                "Product Sales 3",
                dataset3,
                true, 
                true,
                false);

        ChartPanel chartPanel3 = new ChartPanel(pieChart3);
        add(chartPanel3);

        // Exit application when window is closed
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
    }

    public static void main(String[] args) {
        PieChartExample chart = new PieChartExample();
        chart.pack();
        chart.setVisible(true);
    }
}

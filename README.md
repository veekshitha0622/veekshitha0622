.import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

public class NumberCalculator extends JFrame {

    /**
     * Main method to run the application.
     * @param args Command line arguments (not used).
     */
    public static void main(String[] args) {
        // Create a new JFrame with title "Floating Point Numbers Calculator"
        JFrame frame = new JFrame("Floating Point Numbers Calculator");

        // Set the default close operation so the application exits when the window is closed
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);

        // Set the size of the window (400 pixels width, 300 pixels height)
        frame.setSize(400, 300);

        // Set the layout of the frame to FlowLayout (components will be arranged sequentially)
        frame.setLayout(new FlowLayout());

        // Create labels to prompt the user for input
        JLabel label1 = new JLabel("Enter first number:");
        JTextField textField1 = new JTextField(10); // Text field to enter the first number

        JLabel label2 = new JLabel("Enter second number:");
        JTextField textField2 = new JTextField(10); // Text field to enter the second number

        JLabel label3 = new JLabel("Enter third number:");
        JTextField textField3 = new JTextField(10); // Text field to enter the third number

        // Create a button that will trigger the calculation
        JButton calculationButton = new JButton("Calculate");

        // Adding tooltips to the text fields for better user experience
        textField1.setToolTipText("Enter the first floating point number");
        textField2.setToolTipText("Enter the second floating point number");
        textField3.setToolTipText("Enter the third floating point number");

        // Add the components (labels, text fields, button) to the frame
        frame.add(label1);
        frame.add(textField1);
        frame.add(label2);
        frame.add(textField2);
        frame.add(label3);
        frame.add(textField3);
        frame.add(calculationButton);

        // Action listener for the "Calculate" button
        calculationButton.addActionListener(new ActionListener() {
            /**
             * This method is triggered when the "Calculate" button is clicked.
             * It performs the arithmetic calculations (sum, average, largest) 
             * and displays the result in a message dialog.
             * @param e ActionEvent triggered by the button click.
             */
            public void actionPerformed(ActionEvent e) {
                try {
                    // Parse the values from the text fields to float numbers
                    float num1 = Float.parseFloat(textField1.getText());
                    float num2 = Float.parseFloat(textField2.getText());
                    float num3 = Float.parseFloat(textField3.getText());

                    // Calculate the sum, average, and largest of the three numbers
                    float sum = num1 + num2 + num3;
                    float average = sum / 3;
                    float largest = Math.max(num1, Math.max(num2, num3));

                    // Format the result message with the calculations
                    String resultMessage = String.format("Sum: %.2f\nAverage: %.2f\nLargest: %.2f", sum, average, largest);

                    // Display the result in a message dialog
                    JOptionPane.showMessageDialog(frame, resultMessage, "Results", JOptionPane.INFORMATION_MESSAGE);

                } catch (NumberFormatException ex) {
                    // If any of the inputs is not a valid number, show an error message
                    JOptionPane.showMessageDialog(frame, "Please enter valid numbers.", "Error", JOptionPane.ERROR_MESSAGE);
                }
            }
        });

        // Center the frame on the screen when it's launched
        frame.setLocationRelativeTo(null);

        // Make the frame visible to the user
        frame.setVisible(true);
    }
}

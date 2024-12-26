import java.awt.*;
import java.awt.event.*;

public class SimpleCalc extends Frame implements ActionListener {
    TextField num1Field, num2Field, resultField;
    Button addBtn, subBtn, mulBtn, divBtn;

    public SimpleCalc() {
        
        num1Field = new TextField();
        num1Field.setBounds(150, 50, 150, 20);

        num2Field = new TextField();
        num2Field.setBounds(150, 100, 150, 20);

        resultField = new TextField();
        resultField.setBounds(150, 200, 150, 20);
        resultField.setEditable(false); 

        
        Label num1Label = new Label("Enter 1st Number:");
        num1Label.setBounds(50, 50, 100, 20);

        Label num2Label = new Label("Enter 2nd Number:");
        num2Label.setBounds(50, 100, 100, 20);

        Label resultLabel = new Label("Result:");
        resultLabel.setBounds(50, 200, 100, 20);

        
        addBtn = new Button("Add");
        addBtn.setBounds(50, 150, 60, 30);
        addBtn.addActionListener(this);

        subBtn = new Button("Subtract");
        subBtn.setBounds(120, 150, 60, 30);
        subBtn.addActionListener(this);

        mulBtn = new Button("Multiply");
        mulBtn.setBounds(190, 150, 60, 30);
        mulBtn.addActionListener(this);

        divBtn = new Button("Divide");
        divBtn.setBounds(260, 150, 60, 30);
        divBtn.addActionListener(this);

        
        add(num1Label);
        add(num2Label);
        add(resultLabel);
        add(num1Field);
        add(num2Field);
        add(resultField);
        add(addBtn);
        add(subBtn);
        add(mulBtn);
        add(divBtn);

        
        setSize(400, 300);
        setLayout(null); 
        setVisible(true);
    }

    @Override
    public void actionPerformed(ActionEvent e) {
        try {
            
            double num1 = Double.parseDouble(num1Field.getText());
            double num2 = Double.parseDouble(num2Field.getText());
            double result = 0;

            
            if (e.getSource() == addBtn) {
                result = num1 + num2;
            } else if (e.getSource() == subBtn) {
                result = num1 - num2;
            } else if (e.getSource() == mulBtn) {
                result = num1 * num2;
            } else if (e.getSource() == divBtn) {
                if (num2 == 0) {
                    resultField.setText("Error: Div by 0");
                    return;
                }
                result = num1 / num2;
            }

            
            resultField.setText(String.valueOf(result));

        } catch (NumberFormatException ex) {
            resultField.setText("Invalid Input");
        }
    }

    public static void main(String[] args) {
        new SimpleCalc(); 
    }
}

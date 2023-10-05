


using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;

namespace One_Line_A_Day_to_Keep_the_doctor_Awake
{
    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();
        }
        private double Evaluate(string expression)
        {
            System.Data.DataTable table = new System.Data.DataTable();
            table.Columns.Add("expression", typeof(string), expression);
            System.Data.DataRow row = table.NewRow();
            table.Rows.Add(row);
            return double.Parse((string)row["expression"]);
        }

            
        private void contextMenuStrip1_Opening(object sender, CancelEventArgs e)
        {

        }
        private void Button_Click(object sender, EventArgs e)
        {
            Button button = (Button)sender;

            if (button.Text == "C")
            {
                textBoxResult.Text = "";
            }
            else if (button.Text == "=")
            {
                try
                {
                    string expression = textBoxResult.Text;
                    double result = Evaluate(expression);
                    textBoxResult.Text = result.ToString();
                }
                catch (Exception ex)
                {
                    textBoxResult.Text = "Error";
                }
            }
            else
            {
                textBoxResult.Text += button.Text;
            }
        }

        private void textBoxResult_TextChanged(object sender, EventArgs e)
        {

        }
    }
}

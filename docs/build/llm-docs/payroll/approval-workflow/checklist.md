# Approval Checklist

Before you approve requests on the [Approvals Dashboard](https://razorpay.com/docs/build/llm-docs/payroll/approval-workflow/approvers.md), refer to the following checklist to understand what an approver must review in the request. 

 

    
### For Edit Payroll

         Verify the following as an approver when you receive requests for [Edit Payroll](https://razorpay.com/docs/build/llm-docs/payroll/run-payroll.md#additions-and-deductions) actions:
            - Employee name and employee id
            - Payroll month
            - New Additions and the amount added
            - Previous Additions and the amount added
            - New Deductions amount calculated from [Loss of Pay](https://razorpay.com/docs/build/llm-docs/payroll/run-payroll.md#loss-of-pay)
            - Previous Deductions amount calculated from [Loss of Pay](https://razorpay.com/docs/build/llm-docs/payroll/run-payroll.md#loss-of-pay)
            - New Arrears amount
            - Previous Arrears amount 

        When you reject a request, the employee's salary remains unchanged. This is not applicable to [skipping](https://razorpay.com/docs/build/llm-docs/payroll/run-payroll.md#skip-salary>) or [resuming](https://razorpay.com/docs/build/llm-docs/payroll/run-payroll.md#resume-skipped-salary) employees' salaries. 
        

    
### For Finalise Payroll

         Verify the following as an approver when you receive requests for [Finalise Payroll](https://razorpay.com/docs/build/llm-docs/payroll/run-payroll.md#execute-payroll) actions:
            - Payroll month
            - Number of employees whose payroll is finalised
            - Number of employees whose payroll is skipped 
 
            
         You can check the details in the Salary Register linked on the Dashboard. 
        

    
### For Salary Revision

         Verify the following as an approver when you receive requests for [Salary Revision](https://razorpay.com/docs/build/llm-docs/payroll/run-payroll.md#revise-salary):
            - Employee name and employee id
            - Effective date
            - Old CTC
            - New CTC
            - Arrears
            - Variable pay 
 
            
         If you use a [custom salary structure](https://razorpay.com/docs/build/llm-docs/payroll.md#custom-salary-structure), check the following: 
            - Basic Salary
            - Dearness Allowance
            - HRA
            - LTA
            - Special Allowance
            - PF contribution
            - ESI contribution
            - Total Custom Allowances 
 
            
         After you approve any Salary Revision request, we email that employee's manager about the revision. You can also withdraw the request if the revision is no longer applicable. 
        

### Related Information 

- [Payroll Checklist](https://razorpay.com/docs/build/llm-docs/payroll/execute-payroll.md)
- [Approvals Dashboard](https://razorpay.com/docs/build/llm-docs/payroll/approval-workflow/approvers.md)
- [Salary Actions in Payroll](https://razorpay.com/docs/build/llm-docs/payroll/salary.md)

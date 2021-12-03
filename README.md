# Exemple-Yup-Where-

```
```ts
export const createReminderSchema = Yup.object().shape({
  type: Yup.string(),
  medicine: Yup.object()
    .shape({
      medicine_name: Yup.string(),
      medicine_date: Yup.string(),
      medicine_hour: Yup.string(),
      observation: Yup.string(),
    })
    .when('type', {
      is: 'medicine',
      then: Yup.object().shape({
        medicine_name: Yup.string().required(),
        medicine_date: Yup.string()
          .required()
          .test('date', (value = '') => {
            return dateValidator(value);
          }),
        medicine_hour: Yup.string()
          .required()
          .test('hour', (value = '') => {
            return validateHour(value);
          }),
      }),
    }),
  vaccine: Yup.object()
    .shape({
      vaccine_name: Yup.string(),
      vaccine_date: Yup.string(),
      vaccine_hour: Yup.string(),
      observation: Yup.string(),
    })
    .when('type', {
      is: 'vaccine',
      then: Yup.object().shape({
        vaccine_name: Yup.string().required(),
        vaccine_date: Yup.string()
          .required()
          .test('date', (value = '') => {
            return dateValidator(value);
          }),
        vaccine_hour: Yup.string()
          .required()
          .test('hour', (value = '') => {
            return validateHour(value);
          }),
      }),
    }),
  exam: Yup.object()
    .shape({
      specialty: Yup.string(),
      professional_name: Yup.string(),
      query_date: Yup.string(),
      query_hour: Yup.string(),
      observation: Yup.string(),
    })
    .when('type', {
      is: 'exam',
      then: Yup.object().shape({
        specialty: Yup.string().required(),
        professional_name: Yup.string().required(),
        query_date: Yup.string()
          .required()
          .test('date', (value = '') => {
            return dateValidator(value);
          }),
        query_hour: Yup.string()
          .required()
          .test('hour', (value = '') => {
            return validateHour(value);
          }),
      }),
    }),
});
```
```
